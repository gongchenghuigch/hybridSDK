## WBCST.versionCompare(higher, lower)

支持所有版本



## 描述

- 比较车商通APP版本大小



## 参数

| 参数名 | 必选 | 类型   | 说明         |
| ------ | ---- | ------ | ------------ |
| higher | √    | String | 期望较高版本 |
| lower  | √    | String | 期望较低版本 |

#### 

### 返回结果

```
higher > lower: 1;
higher = lower: 0;
higher < lower: -1;
```



## 示例

```
//传入版本号的格式*.*.* 要是三位的固定格式
WBCST.versionCompare(WBCST.getVersion(), 3.7.0)
```

