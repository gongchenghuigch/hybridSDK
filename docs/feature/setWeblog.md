### WBCST.setWeblog(params)

支持所有版本



## 描述

- 添加页面统计埋点 native接的友盟埋点统计系统 不是公司BI埋点统计



## 参数

参数params为对象属性，具体参数：

```
{
    eventId, 
    attributes
}
```

| 参数名     | 必填 | 类型   | 说明               |
| ---------- | ---- | ------ | ------------------ |
| eventId    | √    | String | 埋点点击事件ID     |
| attributes | √    | Object | 页面埋点（键值对） |



## 示例

```
WBCST.setWeblog({ 
    eventId: 'dingyue', 
    attributes: { piliangguanli: '我的订阅' } 
});
```

