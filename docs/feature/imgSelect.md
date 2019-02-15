## WBCST.imgSelect(params, callback)

V3.5.0



## 描述

- 从给定的图片数组里面选择图片，点击预览页面大图轮播预览



## 参数

| 参数名   | 必填 | 类型     | 说明                                                         |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| params   | √    | Object   | 图片选择需要的参数                                           |
| callback | √    | Function | 选择图片回调函数，最好是传入匿名函数，如果传入函数名，必须是全局函数 |

参数params为对象属性，其中参数：

```
{ 
	maxSelectedNum, 
	title, 
	images 
}
```

| 参数名         | 必填 | 类型   | 说明                     |
| -------------- | ---- | ------ | ------------------------ |
| maxSelectedNum | √    | Number | 支持最多选取图片张数     |
| title          | √    | String | 预览图片页面标题         |
| images         | √    | Array  | 可供选择和预览的图片数组 |

参数images结构如下：

```
 images:[
 	{
		isSelected: 0,
		imgUrl: "https://pic2.58cdn.com.cn/p1/big/n_v24ae5294301884442bb373e1edce23938.jpg"
	},
	{
		isSelected：1,
		imgUrl: "https://pic5.58cdn.com.cn/p1/big/n_v2019543e915da4381a96128b9a99c965c.jpg"
	}
]

```

| 参数名     | 必填 | 类型   | 说明                               |
| ---------- | ---- | ------ | ---------------------------------- |
| isSelected | √    | Number | 0：图片未被选中<br />1：图片被选中 |
| imgUrl     | √    | String | 图片地址                           |



## 示例

```
WBCST.imgSelect({
	maxSelectedNum: 1,
	title: "更换图片",
	images: [
        {
            isSelected：1, // 给定一张选中图片
            imgUrl: "https://pic2.58cdn.com.cn/p1/big/n_v24ae5294301884442bb373e1edce23938.jpg"
        },
        {
            isSelected：0,
            imgUrl: "https://pic5.58cdn.com.cn/p1/big/n_v2019543e915da4381a96128b9a99c965c.jpg"
        }
	]
}, (event) => {
    //返回选中图片数组
   
})
//此示例回调函数使用的是箭头函数，如果不支持前头函数的 使用常规函数function
```



## 回调参数

```
//返回选中的图片数组 
{
    images: [
        {
            isSelected：1,
            imgUrl: "https://pic2.58cdn.com.cn/p1/big/n_v24ae5294301884442bb373e1edce23938.jpg"
        }
	]
}
```

