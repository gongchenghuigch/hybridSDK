## WBCST.deviceEvent(params, callback)

v3.8.0



## 描述

- 监听native时间，比如监听Webview顶部返回事件



## 参数

| 参数名   | 必填 | 类型     | 说明     |
| -------- | ---- | -------- | -------- |
| params   | √    | Object   | 监听对象 |
| callback | √    | Function | 回调函数 |

参数params为对象属性，具体参数：

```
{
    type
}
```

| 参数名 | 必填 | 类型   | 说明                                                         |
| ------ | ---- | ------ | ------------------------------------------------------------ |
| type   | √    | String | 监听事件，定义的监听事件必须是和native约定好的有效事件，不能谁边填写；目前只实现了监听，webview返回事件goback；如果业务方调用了事件监听协议，并且监听返回事件，点击左上角返回按钮时，native就不会做返回操作了，直接执行事件监听的callback，由业务方自己处理完业务逻辑后，在做返回操作 |



## 示例

```
WBCST.deviceEvent({ type: 'goback' }, event => {
    WBCST.dialog(
        {
            title: '提示',
            content: '是否保存草稿？',
            btns: [{ text: '取消', color: '#000000' }, { text: '保存', color: '#ff552e' }]
        },
        event => {
            //TODO
           if(event && event.result == 0){
               WBCST.closeCurrentPage();
           }
        }
    );
});
```



## 回调参数

```
//返回事件类型
{
    type: 'goback'
}
```

