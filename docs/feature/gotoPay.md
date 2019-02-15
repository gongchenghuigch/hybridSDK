### WBCST.gotoPay(params, callback)

v3.8.0



### 描述

- 直接调起车商通native支付，跳转收银台



### 参数

| 参数名   | 必填 | 类型     | 说明                                                         |
| -------- | ---- | -------- | ------------------------------------------------------------ |
| params   | √    | Object   | 支付协议传参                                                 |
| callback | √    | Function | 选择图片回调函数，最好是传入匿名函数，如果传入函数名，必须是全局函数 |

参数params为对象属性，其中参数：

```
{
    payOrderData 支付参数
}
```

| 参数名       | 必填 | 类型   | 说明     |
| ------------ | ---- | ------ | -------- |
| payOrderData | √    | Object | 支付参数 |

##  示例

```
WBCST.gotoPay(
    {
        payOrderData: {
            accountType: '1',
            balancePaid: '1',
            cityId: '1',
            endtime: '2019-02-10 16:35:13',
            extensionInfo: '{@cate@:@4,29,111945@}',
            merid: '1371',
            notifyUrl: 'https://cheshangtongapi.58.com/ershouche/subscribe/paycallback',
            orderId: '1083643482393849856',
            orderMoney: '20.00',
            payType: 'wechat|alipay',
            payfrom: '15',
            productDesc: '优选访客批量回复',
            productName: '优选访客批量回复',
            sign: 'af128bd24e119826559838fa8fb33adb',
            starttime: '2019-01-11 16:35:13',
            validPayTime: '30m'
        }
    },
    event => {
        alert(JSON.stringify(event));
    }
);
```



## 回调参数

| 参数名 | 类型   | 说明                     |
| ------ | ------ | ------------------------ |
| result | Number | 0：支付成功；1：支付失败 |

