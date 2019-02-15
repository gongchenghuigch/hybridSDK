## WBCST.share(params, callback)

v3.5.0



## 描述

- 调用native分享



## 参数

| 参数名   | 必填 | 类型             | 说明                                                         |
| -------- | ---- | ---------------- | ------------------------------------------------------------ |
| params   | √    | Object           | 分享需要的参数                                           |
| callback | √    | Function | 选择图片回调函数，最好是传入匿名函数，如果传入函数名，必须是全局函数 |

参数params为对象属性，其中参数：

```
{
    imageType,
    imageBase64,
    imageUrl,
    title,
    text,
    shareUrl
}
```

| 参数名      | 必填 | 类型   | 说明                                                         |
| ----------- | ---- | ------ | ------------------------------------------------------------ |
| imageType   | -    | String | 分享类型：1：native截屏分享（需要截屏分享时必填）<br />2：分享base64类型图片（imageBase64必填）<br />3：分享网络图片 （imageUrl必填）<br />此参数只支持v3.7.2版本以上 |
| imageBase64 | ×    | String | 分享base64图片时必填                                         |
| imageUrl    | ×    | String | 分享图标，默认58 logo图片                                    |
| title       | ×    | String | 分享链接时标题                                               |
| text        | ×    | String | 分享链接时描述                                               |
| shareUrl    | ×    | String | 分享链接时必填                                               |



## 示例

```
//分享链接
WBCST.share(
    {
        imageUrl:
            'https://pic5.58cdn.com.cn/p1/big/n_v2019543e915da4381a96128b9a99c965c.jpg',
        title: '本田 雅阁 2003款 2.4 自动 Vtec舒适版',
        text: '好车不议价',
        shareUrl: 'https://bj.58.com/ershouche/36717121214998x.shtml'
    },
    event => {
    	//TODO
        WBCST.toast({ text: JSON.stringify(event) });
    }
);

//分享网络图片(推荐)
WBCST.share(
    {
        imageUrl:
            'https://pic5.58cdn.com.cn/p1/big/n_v2019543e915da4381a96128b9a99c965c.jpg'
    },
    event => {
        // TODO
        WBCST.toast({ text: JSON.stringify(event) });
    }
);
或者
//此种用法只能在v3.7.2版本以上
WBCST.share(
    {
        imageType: '3',
        imageUrl:
            'https://pic5.58cdn.com.cn/p1/big/n_v2019543e915da4381a96128b9a99c965c.jpg'
    },
    event => {
        // TODO
        WBCST.toast({ text: JSON.stringify(event) });
    }
);

//分享base64图片
WBCST.share(
    {
        //转换的base64图片要去除前缀data:image/png;base64,
        imageBase64:
            'iVBORw0KGgoAAAANSUhEUgAAAGQAAABkCAMAAABHPGVmAAABCFBMVEUAAAD...'
    },
    event => {
        // TODO
        WBCST.toast({ text: JSON.stringify(event) });
    }
);
或者
//此种用法只能在v3.7.2版本以上
WBCST.share(
    {
        imageType: '2',
        //转换的base64图片要去除前缀data:image/png;base64,
        imageBase64:
            'iVBORw0KGgoAAAANSUhEUgAAAGQAAABkCAMAAABHPGVmAAABCFBMVEUAAAD...'
    },
    event => {
        // TODO
        WBCST.toast({ text: JSON.stringify(event) });
    }
);
//截屏幕长图分享v3.7.2
WBCST.share({ imageType: '1' }, event => {
    // TODO
    WBCST.toast({ text: JSON.stringify(event) });
});
```



## 回调参数

```
{
    msg: "",
    platform: "",
    code: ""
}
```



| 参数名   | 类型   | 说明                                                    |
| -------- | ------ | ------------------------------------------------------- |
| msg      | String | 开始分享/分享成功/分享失败/分项取消                     |
| platform | String | Wechat、WechatMoments、WechatFav（微信收藏）、QZone、QQ |
| code     | String | 0：开始，  1：成功，-1：失败，-2：取消                  |

