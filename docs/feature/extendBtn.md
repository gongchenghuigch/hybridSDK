## WBCST.extendBtn(params, callback)

v3.8.0



## 描述

- 配置webview页面导航栏右侧按钮



## 参数

| 参数名   | 必填 | 类型     | 说明     |
| -------- | ---- | -------- | -------- |
| params   | √    | Object   | 配置参数 |
| callback | √    | Function | 回调函数 |

参数params为对象属性，具体参数：

```
{
    btns
}
```

| 参数名 | 必填 | 类型  | 说明                               |
| ------ | ---- | ----- | ---------------------------------- |
| btns   | √    | Array | 按钮配置数组，每个按钮配置对象如下 |

btnObject:

```
{
    action,
    text,
    color,
    icon
}
```

| 参数名 | 必填 | 类型   | 说明                                                         |
| ------ | ---- | ------ | ------------------------------------------------------------ |
| action | √    | String | 按钮点击事件标识，也是native返回前端按钮点击的唯一标识       |
| text   | -    | String | 按钮文案，和icon选填其一                                     |
| color  | ×    | String | 设置按钮文案颜色                                             |
| icon   | -    | String | 按钮图标地址（要使用网络图片地址），和text选填其一；如果text和icon都填写，优先使用icon |



## 示例

```
WBCST.extendBtn(
    {
        btns: [
            {
                action: 'edit',
                text: '编辑',
                color: '#ff552e',
                icon: ''
            },
            {
                action: 'share',
                text: '分享',
                color: '#ff552e',
                icon:
                    'https://img.58cdn.com.cn/images/car/activitypic/cheshangtong/share-big.png'
            }
        ]
    },
    event => {
        //TODO
    }
```



## 回调参数

| 参数名 | 类型   | 说明                                 |
| ------ | ------ | ------------------------------------ |
| action | String | native透传业务方配置的按钮action事件 |

