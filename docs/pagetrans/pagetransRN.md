## WBCST.pagetransRN(params, callback)

v3.7.2



## 描述

- 跳转车商通RN页面



## 参数

| 参数名   | 必填 | 类型     | 说明               |
| -------- | ---- | -------- | ------------------ |
| params   | √    | Object   | 页面跳转需要的参数 |
| callback | ×    | Function | 回调函数           |

参数params为对象属性，具体参数：

```
{
    bundleId, 
    isDestoryBeforePage = 0, 
    jumpParameter
}
```

| 参数名              | 必填 | 类型   | 说明                                                |
| ------------------- | ---- | ------ | --------------------------------------------------- |
| bundleId            | √    | String | RN页面ID                                            |
| isDestoryBeforePage | ×    | Number | 是否销毁上级页面 默认0：不销毁<br />1：销毁上级页面 |
| jumpParameter       | ×    | Object | 需要携带到目的页面的参数                            |

RN页面ID列表：

| ID    | 页面                                         |
| ----- | -------------------------------------------- |
| 10020 | 车商通每日任务                               |
| 10021 | 车商通优选商机订阅                           |
| 10022 | 车商通优选商机订阅（内置native优选访客部分） |



## 示例

```
WBCST.pagetransRN({ 
	bundleId: '10020', 
	jumpParameter:{
        infoId: 11233887876656
	}
}, event => {
       //TODO
});
```

