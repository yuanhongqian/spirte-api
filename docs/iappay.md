# IapPay 苹果虚拟支付工具类

----------

IapPay苹果虚拟支付工具类，主要实现iOS系统对虚拟商品（如电子书，金币）等的购买支付，该组件仅iOS系统支持。

使用时需要在js中引入 ：

```javascript
var iappay = require("IapPay"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录： 


>[ canMakePay(): boolean   是否支持虚拟支付功能 ](#ff_0)
> 
> [getProducts(jsonData:Object,callBackFun:Function): void  获取有效商品详细信息列表 ](#ff_1)
> 
> [pay(dataJson:string, callBackFun:Function): void   购买虚拟商品 ](#ff_2)
>
> [restore(callBackFun:Function): void    恢复用户以前购买过的所有商品交易 ](#ff_3)





<span id="ff_0">**canMakePay()**</span>  

<code>是否支持虚拟支付功能</code>  

参数：无 

返回值：bool型

> true：支持虚拟支付 
> 
> false：不支持虚拟支付

**注：** 支付前需调用该方法判断是否支持虚拟支付





<span id="ff_1">**getProducts(jsonData:Object,callBackFun:Function): void**</span>  

<code>获取有效商品详细信息列表</code>   

参数：  

jsonData：获取商品参数设置，Json对象，定义如下：  

> ids：需要查询的商品id集，字符串数组，必选项；

callBackFun：查询有效商品列表回调，该回调函数具有Json对象入参，定义如下：  

> code ：回应状态码，数字[0,-1]
> 
> -  0：查询成功；
> 
> -  -1：查询失败；
> 
> invalidIds：无效的商品id列表，字符串数组；
> 
> products：有效商品列表，数组，数组中成员为Json对象，定义如下：
> 
> - id：商品id，字符串类型
> 
> - title：商品标题，字符串类型
> 
> - description：商品描述，字符串类型
> 
> - price：商品价格，数字类型

返回值：无 

<span id="ff_2">**pay(dataJson:string, callBackFun:Function): void**</span>  

<code>购买虚拟商品</code> 

参数：  

dataJson：商品支付参数设置，Json对象，定义如下：  

> id：需要支付的商品标识，字符串类型，必选项；
> 
> quantity ：购买商品数量，数字类型，必选项；

callBackFun：购买商品回调，该回调函数具有Json对象入参，定义如下：  

> code ：回应状态码，数字类型，[0,-1,-2]
> 
> -  0：交易成功；
> 
> -  -1：交易失败；
> 
> -  -2：已经购买过该商品；
> 
> id：购买商品id，字符串类型；
> 
> transactionId：交易id，字符串类型；
> 
> transactionReceipt：交易凭证，经过base64编码，用于验证交易是否合法和有效，避免因越狱破解内购后造成损失，只在code为0购买成功时有效，字符串类型；

返回值：无



<span id="ff_3">**restore(callBackFun:Function): void**</span>  

<code>恢复用户以前购买过的所有商品交易</code>  


参数：  

callBackFun：恢复购买商品回调，该回调函数具有Json对象入参，定义如下：

> code ：回应状态码，数字[0,-1]
> 
> -  0：恢复购买商品成功；
> 
> -  -1：恢复购买商品失败；
> 
> transactions：服务器返回已恢复购买的商品信息，数组类型，数组成员为Json对象，定义如下：
>
> id：购买商品id，字符串类型
> 
> transactionId：交易id，字符串类型
> 
> transactionReceipt：交易凭证，经过base64编码，用于验证交易是否合法和有效，避免因越狱破解内购后造成损失，字符串类型
> 
> originalTransactionId：原始交易id，串类型；

返回值：无