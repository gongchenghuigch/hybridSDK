## WBCST.loading(params)

支持所有版本



## 描述

- 页面loading



## 参数

参数params为对象属性，具体参数：

```
{ 
	text = '加载中', 
	state 
}
```

| 参数名 | 必填 | 类型   | 说明                                                         |
| ------ | ---- | ------ | ------------------------------------------------------------ |
| text   | ×    | String | loading文案，默认"加载中"                                    |
| state  | √    | String | loading状态<br />show：显示loading<br />dismiss：隐藏loading |



## 示例

```
WBCST.loading({ text: '放飞吧少年', state: 'show' });
setTimeout(() => {
    WBCST.loading({ state: 'dismiss' });
}, 3000);
```