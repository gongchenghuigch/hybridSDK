## 概述

该SDK提供车商通APP js与 native交互的能力，让前端开发者调用APP的一些原生组件，功能等；

调用分享、页面跳转、配置页面导航栏等，更多功能请[查看Hybrid设计文档](http://c.58corp.com/pages/viewpage.action?pageId=17050960)



## 开始使用

#### 1、SDK引入文件引入

js地址：https://j1.58cdn.com.cn/escstatic/appSdk/cstSdk/cst-new-app.js



### 2、相关API的使用

SDK总共有两类

- 通用协议：提供了最基层的js与native的通信接口，封装invoke方法
- 封装层：提供了已经封装好的API调用，直接根据文档参数直接使用

所有接口都挂载在WBCST上

如果SDK未提供业务类调用的API方法，业务方可参考Hybrid设计文档里面的协议参数设计，直接调用WBCST.invoke来实现



##### 关于页面导航配置的使用必读

在老版本中导航配置杂糅了很多的其他业务功能，对于大多数的业务来说根本使用不到，基于此在新版本中我们对页面导航的功能做了细化的拆分，业务方根据自己的需求配置不同的功能

- navigatorConfig（老版本导航配）
  包含功能：设置title、配置左侧按钮并监听点击事件、配置右侧按钮并监听点击事件、配置页面是否支持下拉刷新和上拉加载、配置页面跳转返回通知接收callback
- 新版本修改
  对以上的导航配置做了优化，新改版导航配置根基功能点做了拆分，把每个功能个单独拆分成单个协议，各司其职。具体包含以下协议方法：

  setTitle 设置标题  
  extendBtn 配置右侧按钮  
  pullRefresh 配置下拉刷新和上拉加载  
  deviceEvent 监听返回事件  



##### 关于协议回调

每个有回调的API，都有两种入参方式：

- 以字符串的方式传入方法名  
  传入方法名时，该方法必须是全局函数

  ```
  //方案一
  WBCST.dialog(params, 'dialogCallback');
  //只传入函数名时 切记函数的写法一定要在WBCST全局对象属性下，不可写其他全局属性
  WBCST.dialogCallback = (event)=>{
      //TODO
  }
  //方案二
  //直接把函数的全局属性一块入参
  WBCST.dialog(params, 'WBCST.dialogCallback');
  WBCST.dialogCallback = (event)=>{
      //TODO
  }
  ```

- 传入匿名函数（推荐）  

  ```
  WBCST.dialog(params, (event)=>{
      //TODO
  });
  ```

注意：

业务方调用时不支持箭头函数的，直接使用常规匿名函数就可以function(event){}