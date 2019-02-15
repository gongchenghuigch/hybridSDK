## WBCST.navigatorConfig(params)

v3.1.0



## 描述

- 配置H5页面导航栏（页面标题、左右侧按钮配置），以及页面下拉和上拉
- 配置按钮时每个按钮都会对应一个callback回调，如果填写，点击时native执行按钮配置的callback回调，如果不填写，native端会响应一些特殊的事件 如：back，share等
- 页面下拉加载和上拉刷新会对应一个callback回调，在这个回调里面处理动画结束的操作
- 页面跳转，返回后接受native通知也会对应一个callback回调，如果从目的页面返回当前页面，需要native通知返回的操作，需要配置此回调



## 参数

参数params为对象属性，具体参数：

```
{
    title,
    isPullRefresh = false,
    isPullUpLoad = false,
    leftBtn = [{ id: '1', text: '返回', click: 'back' }],
    rightBtn,
    callback,
    autoRefreshCallback
}
```

| 参数名              | 必填 | 类型     | 说明                                     |
| ------------------- | ---- | -------- | ---------------------------------------- |
| title               | √    | String   | 页面标题设置                             |
| isPullRefresh       | ×    | Boolean  | 是否支持下拉刷新 默认false不支持         |
| isPullUpLoad        | ×    | Boolean  | 是否支持上拉加载更多 默认false不支持     |
| leftBtn             | ×    | Array    | 导航栏左侧按钮配置 默认配置返回按钮      |
| rightBtn            | ×    | Array    | 导航栏右侧按钮配置                       |
| callback            | ×    | Function | 响应下拉刷新或者上拉加载的回调函数       |
| autoRefreshCallback | ×    | Function | 响应页面跳转返回到本页面native通知的回调 |

说明：

- 由于之前协议制定时不是很规范，导航上配置按钮时，每个按钮点击事件的响应都必须有自己单独的回调，默认配置的返回按钮是没有回调事件响应的，如果需要响应点击事件，需要重新配置，并且配置回调函数
- 如果下拉刷新和上拉加载配置了其一，必须传入callback
- 如果需要页面跳转，从目的页面返回当前页面需要native同时，必须传入autoRefreshCallback

按钮参数配置：

```
[
	{
        id:"1",
        text:"",
        click:"shop",
        picUrl:"https://img.58cdn.com.cn/images/car/activitypic/cheshangtong/shop-big.png",
        callback:(event)=>{
            //返回点击事件
        }
    },
    {
        id:"2",
        text:"",
        click:"share",
        picUrl:"https://img.58cdn.com.cn/images/car/activitypic/cheshangtong/share-big.png",
        data:{userId:userId},
        callback:(event)=>{
            //返回点击事件
        }
    }
 ]

```

| 参数名   | 必填 | 类型     | 说明                            |
| -------- | ---- | -------- | ------------------------------- |
| id       | √    | String   | 按钮索引                        |
| text     | ×    | String   | 按钮文案 无picUrl图片地址时必填 |
| click    | ×    | String   | 响应事件                        |
| picUrl   | ×    | String   | 按钮显示图片 无text文案时必填   |
| data     | ×    | Object   | 按钮响应事件需要的数据          |
| callback | ×    | Function | 按钮点击响应事件的回调结果      |

参数click特殊响应事件：

| 事件名 | 类型   | 说明                                                      |
| ------ | ------ | --------------------------------------------------------- |
| back   | String | 配置左上角返回按钮，不填写callback时,native直接返回上一页 |



注意：

text按钮文案和picUrl按钮图片必须跳其中之一，如果两者都填写，优先展示图片。

按钮回调结果：

```
//返回按钮配置的所有信息，选择性使用
{
    id:"2",
        text:"",
        click:"share",
        picUrl:"https://img.58cdn.com.cn/images/car/activitypic/cheshangtong/share-big.png",
        data:{userId:userId},
        callback:"__CSTJSBridge_Callback_1547537758644"
}
```



## 示例

```
WBCST.navigatorConfig({
    title: '测试导航',
    isPullRefresh: true,
    isPullUpLoad: true,
    leftBtn: [
        {id: '1', text: '返回', click: 'back'}
        {id: '1', text: '关闭', click: 'close'}
    ],
    rightBtn: [
        {
            id: '1',
            text: '',
            click: 'shop',
            picUrl:
                'https://img.58cdn.com.cn/images/car/activitypic/cheshangtong/shop-big.png',
            callback: event => {
                alert(JSON.stringify(event) + 'ceshi1');
            }
        },
        {
            id: '2',
            text: '',
            click: 'share',
            picUrl:
                'https://img.58cdn.com.cn/images/car/activitypic/cheshangtong/share-big.png',
            callback: event => {
                alert(JSON.stringify(event) + 'ceshi2');
            },
            data: { userId: 'aaa' }
        }
    ],
    callback: event => {
        //返回下拉刷新或者上拉加载的结果
        alert(JSON.stringify(event));
        WBCST.endAnimate({ endMode: event });
    },
    autoRefreshCallback: event => {
        alert(JSON.stringify(event) + '111');
    }
});
 //此示例回调函数使用的是箭头函数，如果不支持前头函数的 使用常规函数function       
```



## 回调参数

callback回调

| 参数名 | 类型   | 说明                                                         |
| ------ | ------ | ------------------------------------------------------------ |
| -      | Number | 直接返回Namber类型的回调结果<br />1：下拉刷新完成 需要调用关闭下拉刷新动画的协议<br />2：上拉加载完成 需要调用关闭上拉加载动画的协议 |

autoRefreshCallback回调

无回调参数，native直接调用传入的autoRefreshCallback函数，变成可执行函数