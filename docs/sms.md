# Sms 短信操作类

----------

 Sms 短信操作类 主要用于发送短信。

使用时需要在js中引入 ：

```javascript
var sms = require("Sms"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ sendSms(jsonData:Object): void 打开短信发送界面发送短信 ](#ff_0)
> 
> [sendSmsAsyn(jsonData:Object,callBackFun:Function): void 后台发送短信 ](#ff_1)
 

<span id="ff_0">**sendSms(jsonData:Object): void**</span>  

<code>打开短信发送界面发送短信</code>     

参数：  

jsonData：短信发送传递参数，json类型，必选项，定义如下：  

>   phone：需要发送的手机号码集，字符串数组，必选项；
>   
>   content：需要发送内容，字符串类型，可选项；

返回值：无


<span id="ff_1">**sendSmsAsyn(jsonData:Object,callBackFun:Function): void**</span>  

<code>后台发送短信</code>   

参数：  

jsonData：短信发送传递参数，json类型，必选项，定义如下：

>   phone：需要发送的手机号码，字符串类型，必选项；
>   
>   content：需要发送内容，字符串类型，必选项；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：发送短信成功；
> 
> - -1：发送短信失败；

返回值：无 

**注：**  仅Android支持