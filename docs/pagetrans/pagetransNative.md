## WBCST.pagetransNative(params)

支持所有版本



## 描述

- 跳转车商通原生页面



## 参数

| 参数名 | 必填 | 类型   | 说明               |
| ------ | ---- | ------ | ------------------ |
| params | √    | Object | 页面跳转需要的参数 |

参数params为对象属性，具体参数：

```
{
    pageType, 
    page,
    tabIndex,
    isDestoryBeforePage = 0, 
    jumpParameter
}
```

| 参数名              | 必填 | 类型   | 说明                                                         |
| ------------------- | ---- | ------ | ------------------------------------------------------------ |
| pageType            | √    | String | 页面名称                                                     |
| page                | ×    | String | 也是页面名称,部分页面需要和pageType两者一块才能确定,pageType是content_nativepage的页面 page必填 |
| tabIndex            | ×    | Number | 带tab页签切换的页面，需要跳转tab页签的索引值                 |
| isDestoryBeforePage | ×    | Number | 是否销毁上级页面 默认0：不销毁<br />1：销毁上级页面          |
| jumpParameter       | ×    | Object | 需要携带到目的页面的参数                                     |

native页面列表：

| pageType                | page              | 说明                                                         |
| ----------------------- | ----------------- | ------------------------------------------------------------ |
| content_nativepage      | _cluePage         | tabIndex:1 收车线索页面 <br />tabIndex:0 卖车线索页面        |
| content_nativepage      | _crmPage          | tabIndex:1 客户管理 客户列表页 <br />tabIndex:0 客户管理 来电列表页 |
| content_nativepage      | _marketingPage    | 营销推广页面                                                 |
| content_nativepage      | _stockManagerPage | 库存管理类别选择页面                                         |
| stockcarhome_nativepage | -                 | 二手车库存管理页面                                           |
| coupon_nativepage       | -                 | 优惠券列表页                                                 |
| allfunction_nativepage  | -                 | 全部功能页面                                                 |
| message_nativepage      | -                 | 微聊消息列表页面                                             |
| stockcarlist_nativepage | -                 | 二手车库存管理列表页面                                       |

stockcarlist_nativepage 筛选条件

```
{
    condition:{
		stockStatus:1/2/3/4 //全部，在售，已售，退库
		synStatus:1/2/3/4 //不限，未同步，同步成功，同步失败
	}
}
```



## 示例

```
  WBCST.pagetransNative({
    pageType: 'stockcarlist_nativepage',
    jumpParameter: {
        condition: {
            synStatus: 2
        }
    }
});
WBCST.pagetransNative({
    pageType: 'content_nativepage',
    page: '_cluePage',
    tabIndex: 1
});
```