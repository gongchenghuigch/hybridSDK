## 背景

Hybrid部分协议在最初设计的时候，对于一些客户端自定义的控件设计的大而全，导致在实际的业务场景中使用起来繁琐不好维护。
现在项目中同时有两种协议的存在，Hybrid协议和RN协议，协议的设计差别很大，对于客户端来说，增加了两种协议兼容处理的开发成本。



## 简介

该文档主要是针对已有的Hybrid部分协议设计重新修改，并规范新的协议制定规则



## 规则

Hybrid协议是基于URI，用于响应H5的交互，映射为客户端某一个功能/控件的调用/页面跳转



##### 跳转协议格式

- scheme：wubacst 前后端双方约定好的唯一通信协议标识

- host：jumppage/handlejs 页面跳转/功能及控件调用

- path：唯一确定客户端某一功能/控件/页面的标识

  > 为减少客户端的兼容处理，后续新增协议Hybrid的path和RN的action调用同一功能/控件，要使用同一个字符串 比如：CSTNativeFunctionCity（获取地理位置）、CSTNativeFunctionPay（支付）等

- query：{}  json结构，控件的文案及响应时间的配置/页面跳转需要的参数等



##### 关于参数的说明

- 后续新增协议path要唯一确定一个协议功能 如下：

  ```
  //旧版
  {
      "host": "handlejs",
      "path": "showComponent",
      "query": {
          "alertType": "dialog",
          "viewType": viewtype,
          "elements": elements,
          "callback": callback
      }
  }
  path和query里面的alertType两者才能确定对话框控件 增加不必要的参数拼接
  
  //新版
  { 
  	host: 'handlejs', 
  	path: 'CSTShowDialog', 
  	query: { 
  		title, 
  		content, 
  		btns
      } 
  }
  CSTShowDialog唯一确定对话框控件
  ```

- 关于query参数 尽可能简单化、不要包装过多层次 如下：

  ```
  //旧版
  {
      "host": "handlejs",
      "path": "showComponent",
      "query": {
          "alertType": "dialog",
          "viewType": viewtype,
          "elements": elements,
          "callback": callback
      }
  }
  参数elements
  {
      title: { text: title, color:  color},
      content: { text: content, color:  color },
      button: {
          firstBtn: { id: "1", text: ftext, color: fcolor, click: faction },
          secondBtn: { id: "2", text: stext, color: scolor, click: saction }
      }
  }
  从上面可以看到 对话框上面光标题都需要两次的嵌套，对于协议封装有非常局限的可扩展性，并且一多半都是业务方根本不会使用的废参数，协议制定时的参数利用率极低；
  
  //新版
  { 
  	host: 'handlejs', 
  	path: 'CSTShowDialog', 
  	query: { 
  		title: title 
  		content: content 
  		btns: [{ text: '取消', color: '#000000' }, { text: '确定', color: '#ff552e' }],
  		callback: callback
      } 
  }
  参数简单明了 完全能满足业务方的使用，并且参数利用率100%
  ```

- 关于callback回调 对于包含回调的协议，callback参数都统一放置到query的顶层

  ```
  //旧版SDK
  {
      "host": "handlejs",
      "path": "share",
      "query": {
          "data": {
              url: url,
              imageUrl: imageUrl,
              title: title,
              text: text,
              callback: callback
          }
      }
  }
  {
      "host" : "handlejs",
      "path" : "newShare",
      "query":{
          "data": data,
          "callback":param.shareCallback || ""
      }
  }
  制定协议是都是随心所欲的，callback参数是想怎么放就怎么放，完全没有一个统一的位置，有些包裹在query里的某一参里面，有些直接在query层，根本没法一目了然的看到协议是否有回调函数，基本上没有统一处理的可能性
  
  //新版SDK 或者以后新增协议
  {
      "host" : "handlejs",
      "path" : "xxx",
      "query":{
          "key": value,
          ...
          "callback": callback
      }
  }
  直接把协议回调放在query里面，可以统一处理成匿名函数
  ```


注意：

以后业务方需要和native端新增协议时一定要遵循以上规则，协议制定完成以后，就可以直接调用通用协议invoke方法完成通信交互，invoke都是根据以上规则统一封装处理的