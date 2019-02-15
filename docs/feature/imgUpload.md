## WBCST.imgUpload(params, callback)

支持所有版本



## 描述

- 支持从手机相册选择图片上传、支持实拍图片上传、支持实拍视频上传



## 参数

| 参数名   | 必填 | 类型     | 说明           |
| -------- | ---- | -------- | -------------- |
| params   | √    | Object   | 对话框参数配置 |
| callback | ×    | Function | 回调函数       |

参数params为对象属性，其中参数：

```
{
    maxNum,
    title,
    isNeedTakingPic,
    selectDesc,
    data,
    videoNum
}
```

参数详解：

| 参数名          | 必填 | 类型   | 说明                                                         |
| --------------- | ---- | ------ | ------------------------------------------------------------ |
| maxNum          | √    | Number | 支持最多选取上传图片张数                                     |
| title           | ×    | String | 预览图片页面标题（目前没有使用）                             |
| isNeedTakingPic | ×    | Number | 是否实拍 1：图片和实拍都实拍<br />0：图片可从相册选取也可实拍 |
| selectDesc      | ×    | String | 图片选择页面文案提示                                         |
| data            | ×    | Object | 传给native端图片地址或者实拍地址                             |
| videoNum        | ×    | Number | 是否支持实拍视频功能，支持拍摄视频个数                       |

参数data数据详解：

```
{
    "imgarr": [{
        "localPath": "/storage/emulated/0/58cheshangtong/images/1520931421404.jpeg",
        "networkPath": "https://pic5.58cdn.com.cn/p1/big/n_v278b44fa120524ec680cc57aaa15ccb08.jpg"
    }, {
        "localPath": "/storage/emulated/0/58cheshangtong/images/1520931807285.jpeg",
        "networkPath": "https://pic2.58cdn.com.cn/p1/big/n_v22b10cbf5d1804dd99238d1e475045368.jpg"
    }],
    "paramname": "pic",
    "videoArr": [{
        "localPath": "/storage/emulated/0/58cheshangtong/video/1521528485277.mp4",
        "networkPath": "https://testv1.wos.58dns.org/XZyuTsRqPoXEA/cheshangtongandroid/1521528485277.mp4"
    }]
}
```



| 参数名    | 类型   | 说明                                                         |
| --------- | ------ | ------------------------------------------------------------ |
| paramname | String | 对应上传的参数名                                             |
| imgarr    | Array  | 图片地址<br />localPath：图片在设备本地地址<br />networkPath：图片网络地址 |
| videoArr  | Array  | 视频地址<br />localPath：视频在设备本地地址<br />networkPath：视频网络地址 |



## 示例

```
WBCST.imgUpload(
    {
        maxNum: 8,
        title: '测试图片选择',
        isNeedTakingPic: 0,
        selectDesc: '为保证网站信息真实性，请对证件进行实拍，暂不支持上传相册照片',
        data: {
        "imgarr": [{
            "localPath": "/storage/emulated/0/58cheshangtong/images/1520931807285.jpeg",
            "networkPath": 				"https://pic2.58cdn.com.cn/p1/big/n_v22b10cbf5d1804dd99238d1e475045368.jpg"
            }],
            "paramname": "pic"
		},
        videoNum: 1
    },
    function(event) {
        if (event && event.imgarr.length > 0) {
            let img = event.imgarr[0].networkPath;
            this.setState({
                imgUrl: img
            });
        }
    }
);
```



### 回调参数

回调结果和data传参格式一致

| 参数名    | 类型   | 说明                                                         |
| --------- | ------ | ------------------------------------------------------------ |
| paramname | String | 对应上传的参数名                                             |
| imgarr    | Array  | 图片地址<br />localPath：图片在设备本地地址<br />networkPath：图片网络地址 |
| videoArr  | Array  | 视频地址<br />localPath：视频在设备本地地址<br />networkPath：视频网络地址 |

```
{
    "imgarr": [{
        "localPath": "/storage/emulated/0/58cheshangtong/images/1520931421404.jpeg",
        "networkPath": "https://pic5.58cdn.com.cn/p1/big/n_v278b44fa120524ec680cc57aaa15ccb08.jpg"
    }, {
        "localPath": "/storage/emulated/0/58cheshangtong/images/1520931807285.jpeg",
        "networkPath": "https://pic2.58cdn.com.cn/p1/big/n_v22b10cbf5d1804dd99238d1e475045368.jpg"
    }],
    "paramname": "pic",
    "videoArr": [{
        "localPath": "/storage/emulated/0/58cheshangtong/video/1521528485277.mp4",
        "networkPath": "https://testv1.wos.58dns.org/XZyuTsRqPoXEA/cheshangtongandroid/1521528485277.mp4"
    }]
}
```

h