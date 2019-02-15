## WBCST.getLocation(callback)

v3.8.0



## 描述

- 获取定位信息包括：城市、区域、商圈



## 参数

| 参数名   | 必填 | 类型     | 说明     |
| -------- | ---- | -------- | -------- |
| callback | √    | Function | 回调函数 |



## 示例

```
WBCST.getLocation((event) => {
    //返回定位信息 返回城市、区域、商圈信息  
});
```



## 回调参数

```
event = {
        cityId: "1",
        cityName: "北京",
        cityDirname: "bj",
        businessId: "7551",
        businessName: "大山子",
        businessDirname: "dashanzi",
        areaId: "1142",
        areaName: "朝阳",
        areaDirname: "chaoyang"
    }
    //未开启定位
    event = {
        cityId: "0",
        cityName: "",
        cityDirname: "",
        businessId: "0",
        businessName: "",
        businessDirname: "",
        areaId: "0",
        areaName: "",
        areaDirname: ""
    }
```



| 参数名          | 类型   | 说明         |
| --------------- | ------ | ------------ |
| cityId          | String | 城市ID       |
| cityName        | String | 城市中文名称 |
| cityDirname     | String | 城市拼音缩写 |
| areaId          | String | 区域ID       |
| areaName        | String | 区域中文名称 |
| areaDirname     | String | 区域拼音     |
| businessId      | String | 商圈ID       |
| businessName    | String | 商圈中文名称 |
| businessDirname | String | 商圈拼音     |

