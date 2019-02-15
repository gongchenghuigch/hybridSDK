## WBCST.toast(params)

支持所有版本



## 描述

- 页面轻提示



## 参数

参数params为对象属性，具体参数：

```
{ 
	text, 
	state = 'prompt' 
}
```

| 参数名 | 必填 | 类型   | 说明                                                         |
| ------ | ---- | ------ | ------------------------------------------------------------ |
| text   | √    | String | 提示文案                                                     |
| state  | ×    | String | 提示等级<br /> prompt：一般提示<br />warn：警告提示<br />error：错误提示<br />默认一般提示 |



## 示例

```
WBCST.toast({ text: '测试toast' });
```

