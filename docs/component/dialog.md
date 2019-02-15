## WBCST.dialog(params, callback)

支持所有版本（此协议callback只支持匿名函数）



## 参数

| 参数名   | 必填 | 类型     | 说明                    |
| -------- | ---- | -------- | ----------------------- |
| params   | √    | Object   | 对话框参数配置          |
| callback | ×    | Function | 回调函数 只支持匿名函数 |

参数params为对象属性，具体参数：

```
{
    title,
    content,
    btns
}
```

| 参数名  | 必填 | 类型   | 说明                                           |
| ------- | ---- | ------ | ---------------------------------------------- |
| title   | ×    | String | 对话框标题                                     |
| content | √    | String | 对话框文本                                     |
| btns    | ×    | Array  | 对话框按钮配置，<br />默认是取消和确定两个按钮 |

btns按钮配置参数

| 参数名 | 必填 | 类型   | 说明     |
| ------ | ---- | ------ | -------- |
| text   | √    | String | 按钮文案 |
| color  | ×    | String | 按钮颜色 |



## 示例

```
WBCST.dialog({ 
    title: '温馨提示', 
    content: '确认兑换优惠券？',
    btns: [
        { text: '放弃', color: '#000000'},
        { text: '兑换', color: '#ff552e'}
    ]
}, event => {
     //TODO
});
```



## 回调参数

| 参数名 | 类型   | 说明                 |
| ------ | ------ | -------------------- |
| result | Number | 返回点击按钮的索引值 |

```
{
    result: 0/1
}
```

