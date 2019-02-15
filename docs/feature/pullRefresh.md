## WBCST.pullRefresh(params, callback)

V3.8.0



## 描述

- 配置webview页面的下拉刷新和上拉加载



## 参数

| 参数名   | 必填 | 类型     | 说明     |
| -------- | ---- | -------- | -------- |
| params   | √    | Object   | 配置参数 |
| callback | √    | Function | 回调函数 |

参数params为对象属性，具体参数：

```
{
    pullDownRefresh,
    pullUpLoadMore
}
```

| 参数名          | 必填 | 类型    | 说明                           |
| --------------- | ---- | ------- | ------------------------------ |
| pullDownRefresh | -    | Boolean | 配置下拉刷新，默认false不支持  |
| pullUpLoadMore  | -    | Boolean | 配置上拉加载 ，默认false不支持 |

说明：

如果业务方要使用此协议，两个参数至少要用一个为true，否则毫无意义，native端也没有回调通知



## 示例

```
WBCST.pullRefresh(
    {
        pullDownRefresh: true,
        pullUpLoadMore: true
    },
    event => {
        if (event) {
            let res = event.result;
            //TODO 处理业务逻辑 处理完成关闭动画
            WBCST.endAnimate({ endMode: res });
        }
    }
);
```



## 回调参数

| 参数名 | 类型   | 说明                                                         |
| ------ | ------ | ------------------------------------------------------------ |
| result | Number | result：1 开始下拉刷新的回调<br />result：2开始上拉加载更多的回调 |

