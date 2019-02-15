## WBCST.invoke(action, params,callback)

支持所有版本



## 描述

SDK协议层方法



##### 关于车商通协议约定规则

最终发给native端的消息都会拼接成URL的形式；

URL格式：

scheme://host/path?query

- scheme：通信协议头 wubacst

- host：通信方式 handlejs（事件处理类型）/jumppage（页面跳转类型）

- path：协议名称 具体通信的协议名称

- query：协议参数

  ```
  关于query参数的说明
  {
      key:value,
      key:value,
      ...
      callback:callback
  }
  ```

  query是协议交互的所有参数，是Object类型，如果在和native新约定协议的话要遵循以下规则：

  - 所有约定参数都放在query顶层，不要再包装很深的层次
  - 如果协议有回调，在query下约定协议的callback回调参数，协议回调的key值固定就是callback



## 参数

上面提到车商通协议交互有两种类型，此通用协议只支持handlejs类型

| 参数名   | 必填 | 类型     | 说明                              |
| -------- | ---- | -------- | --------------------------------- |
| action   | √    | String   | 协议名称 也就是协议约定的参数path |
| params   | ×    | Object   | 协议参数 根据具体协议填写参数     |
| callback | ×    | Function | 回调函数                          |



## 示例

```
1、带参数 带回调的调用方式(页面对话框协议)
WBCST.invoke('CSTShowDialog',{
    title: '温馨提示',
    content: '确定要花费200积分对话优惠券吗？',
    btns: [
    	{ text: '取消', color: '#000000' }, 
    	{ text: '确定', color: '#ff552e' }
    ]
},(event)=>{
    //TODO
})

2、只有回调函数无额外参数时，回调方法可以占用params的参数位置
WBCST.invoke('CSTNativeFunctionCity',(event)=>{
    //TODO
})

3、无回调函数
WBCST.invoke('showComponent'{
    alertType: 'toast',
    text: '轻提示',
    state: 'prompt'
})

4、无参数无回调
WBCST.invoke('closeCurrentPage')
```


