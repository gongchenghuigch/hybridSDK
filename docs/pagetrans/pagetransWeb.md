## WBCST.pagetransWeb(params, callback)

V3.8.0支持callback回调，以下版本即使传入callback也不会生效



## 描述

- 跳转其他H5页面



## 参数

| 参数名   | 必填 | 类型     | 说明               |
| -------- | ---- | -------- | ------------------ |
| params   | √    | Object   | 页面跳转需要的参数 |
| callback | ×    | Function | 回调函数           |

参数params为对象属性，具体参数：

```
{
    title, 
    url, 
    isDestoryBeforePage = 0, 
    jumpParameter
}
```

| 参数名              | 必填 | 类型   | 说明                                                         |
| ------------------- | ---- | ------ | ------------------------------------------------------------ |
| title               | √    | String | 设置目的页面标题                                             |
| url                 | √    | String | 要跳转的目的页面链接地址                                     |
| isDestoryBeforePage | ×    | Number | 是否销毁上级页面 默认0：不销毁<br />1：销毁上级页面          |
| jumpParameter       | ×    | Object | 需要携带到目的页面的参数，里面的参数都会拼接在目的页面的URL上，如果传参包含中文的一定要encodeURIComponent编码 |

目的URL上native固定拼接参数

| 参数名      | 类型   | 说明                   |
| ----------- | ------ | ---------------------- |
| os          | String | 操作系统               |
| versionCode | String | 车商通版本             |
| clientsrc   | String | 车商通客户端标识cstapp |

jumpParameter参数：

| 参数名                | 必填 | 类型    | 说明                                                         |
| --------------------- | ---- | ------- | ------------------------------------------------------------ |
| isAppendCommonParam   | ×    | Boolean | Native端通用参数拼接控制，如不需要传false或者不传此参数      |
| isWholeDocumentDraw   | ×    | Number  | android端webview截长屏参数，关乎性能，如果不用请传0或者不传 0/1 |
| isHardwareAccelerated | ×    | Number  | 硬件加速参数,Android端兼容H5页面canvas截屏，保存截屏需要取消加速，传0或者不传 0/1 |
| 其他                  | ×    | -       | 根据业务需求是否需要携带参数                                 |



## 示例

```
WBCST.loadPage({
    title: '测试跳转',
    url: 'https://meizhouapi.58.com/v2/appdetect/index/guarantee_sellcar_buy',
    jumpParameter: {
        infoid:infoId,
        platform:platform,
        postsourceid:31,
        cateid:cateId,
        displocalid:displocalId
    }
},()=>{
    //无回调参数
});
//此示例回调函数使用的是箭头函数，如果不支持前头函数的 使用常规函数function
```

