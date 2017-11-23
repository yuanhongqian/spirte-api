# WeiXin 微信操作工具类

----------

 WeiXin微信操作工具类，实现微信单点登录（OAuth2.0），用户信息获取，分享文本，分享图片，分享图文信息，微信支付等功能。

使用时需要在js中引入 ：

```javascript
var weixin = require("WeiXin"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录： 

>**微信登陆**
>
>[isWeixinInstalled(): boolean   微信是否安装 ](#ff_0)
> 
> [getAuthCode(jsonData:Object,callBackFun:Function): void  启动微信进行登录用户授权认证 ](#ff_1)
> 
> [getAccessToken (jsonData:Object,callBackFun:Function): void   通过code码向微信平台获取access_token等信息 ](#ff_2)
>
> [authAccessToken (jsonData:Object,callBackFun:Function): void    检验授权凭证accessToken是否有效 ](#ff_3)
>
> [refreshAccessToken (jsonData:Object,callBackFun:Function): void    刷新或续期accessToken使用 ](#ff_4)
>
> [getUserInfo(jsonData:Object,callBackFun:Function): void    开发者可通过OpenID来获取用户基本信息 ](#ff_5)
> 
>**微信支付**
>
> [isSupportPay(): boolean    是否支持微信支付 ](#ff_6)
>
> [payOrder(jsonData:Object,callBackFun:Function): void    调用微信支付订单，并返回授权结果 ](#ff_7)
>
>**微信分享**
>
> [shareText(jsonData:Object,callBackFun:Function): void   分享文本到微信好友/微信朋友圈 ](#ff_8)
>
> [shareImage(jsonData:Object,callBackFun:Function): void   分享图片到微信好友/微信朋友圈 ](#ff_9)
>
> [shareNews(jsonData:Object,callBackFun:Function): void  分享新闻（图文信息）到微信好友/微信朋友圈 ](#ff_10)


<span id="ff_0">**isWeixinInstalled(): boolean**</span>  

<code>微信是否安装</code>  

参数：无

返回值：boolean型：

> true：微信已安装
> 
> false：微信未安装





<span id="ff_1">**getAuthCode(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动微信进行登录用户授权认证</code> 

启动微信进行登录用户授权认证，并返回授权结果

参数：  

jsonData：Json对象，定义如下：

> scope：应用授权作用域，字符串枚举型，[snsapi_userinfo]，必选参数       
> 
> - snsapi_userinfo：获取用户个人信息则填写snsapi_userinfo；
> 
> state	：用于保持请求和回调的状态，授权请求后原样带回给第三方。字符串类型，该参数可用于防止csrf攻击（跨站请求伪造攻击），建议带上该参数，可设置为简单的随机数加session进行校验，可选参数

callbackFun：微信登录用户授权认证回调，该函数具有json类型入参，入参定义如下：

> code ：回应状态码，数字,[0,-4,-2]
> 
> - 0：用户同意
> 
> - -4：用户拒绝授权
> 
> - -2：用户取消
> 
> authCode：用户换取access_token的code，仅在code为0时有效
> 
> state：第三方程序发送时用来标识其请求的唯一性的标志，由第三方程序调用sendReq时传入，由微信终端回传，state字符串长度不能超过1K
> 
> lang：微信客户端当前语言
> 
> country：微信用户当前国家信息

返回值：无

注：关于scope参数相关说明，请参见移动应用微信开发指南相关章节

示例：

```javascript
var WeiXin = require("WeiXin");

//生成len长度的随机码
function generateRandomAlphaNum(len) {
    var rdmString = "";
    for (; rdmString.length < len; rdmString += Math.random().toString(36).substr(2));
     return rdmString.substr(0, len);
}

function _getAuthCode(){
    var jsonData = {};
    jsonData.scope = "snsapi_userinfo";
    jsonData.state = "weixin_auth_state_" + generateRandomAlphaNum(8);
    WeiXin.getAuthCode(jsonData,authCall);
}

function authCall(jsonData){
    var result = "";
    var state = document.getElement("getAuthCode_01").getAttr("state");
    if(jsonData.code == 0){
        authCode = jsonData.authCode;
        result = "同意授权，状态码为:" + jsonData.code + "\n认证码为:" + jsonData.authCode + "\n客户端语言:" + jsonData.lang + "\n国家信息:" + jsonData.countryt + "唯一性标识异常：" + jsonData.state;             
    }else if(jsonData.code == -4){
        result = "拒绝授权，状态码为:" + jsonData.code;
    }else if(jsonData.code == -2){
        result = "取消授权,状态码为：" + jsonData.code;
    }else{
        result = "回应状态码异常：" + jsonData.code;
    }
    console.log(result);
}
```




<span id="ff_2">**getAccessToken (jsonData:Object,callBackFun:Function): void**</span>  

<code>通过code码向微信平台获取access_token等信息</code> 

参数：

jsonData：Json对象，定义如下：  

> authCode：填写通过getAuthCode函数获取微信登录getAuthCode 

callbackFun：微信登录用户授权认证回调，该函数具有json类型入参，入参定义如下：  

> code ：回应状态码，数字
> 
> - 0：成功
> 
> - 其他值：失败，若微信服务器连接失败则返回7001错误码，其他错误码参见微信错误码定义
> 
> accessToken：接口调用凭证，字符串
> 
> expiresIn：accessToken接口调用凭证超时时间，数字，单位（秒）
> 
> refreshToken：用户刷新accessToken，字符串
> 
> openId：授权用户唯一标识，字符串
> 
> scope：用户授权的作用域，使用逗号（,）分隔，字符串
> 
> errMsg：错误消息值，字符串类型，当code为非0时，有效

返回值：无



<span id="ff_3">**authAccessToken (jsonData:Object,callBackFun:Function): void**</span>  

<code>检验授权凭证accessToken是否有效</code> 

参数：  

jsonData：Json对象，定义如下： 

> accessToken：接口调用凭证，必选项，字符串
> 
> openId：授权用户唯一标识，必选项，字符串

callbackFun：微信登录用户授权认证回调，该函数具有json类型入参，入参定义如下：  

> code ：回应状态码，数字  
> 
> - 0：成功  
> 
> - 其他值：失败，若微信服务器连接失败则返回7001错误码，其他错误码参见微信错误码定义
> 
> errMsg：错误消息值，字符串类型，当code为非0时，有效  

返回值：无



<span id="ff_4">**refreshAccessToken (jsonData:Object,callBackFun:Function): void**</span>  

<code>刷新或续期accessToken使用</code> 

参数：  

jsonData：Json对象，定义如下：

> refreshToken：填写通过getAccessToken函数获取到的刷新标识，字符串类型

callbackFun：微信登录用户授权认证回调，该函数具有json类型入参，入参定义如下：  

> code ：回应状态码，数字
> 
> -   0：成功
> 
> -   其他值：失败，若微信服务器连接失败则返回7001错误码，其他错误码参见微信错误码定义
> 
> accessToken：接口调用凭证，字符串
> 
> expiresIn：accessToken接口调用凭证超时时间，数字，单位（秒）
> 
> refreshToken：用户刷新accessToken，字符串
> 
> openId：授权用户唯一标识，字符串
> 
> scope：用户授权的作用域，使用逗号（,）分隔，字符串
> 
> errMsg：错误消息值，字符串类型，当errcode为非0时，有效  

返回值：无





<span id="ff_5">**getUserInfo(jsonData:Object,callBackFun:Function): void**</span>  

<code>开发者可通过OpenID来获取用户基本信息</code>   


参数：  

jsonData：Json对象，定义如下：  

> accessToken：接口调用凭证，必选项，字符串
> 
> openId：授权用户唯一标识，必选项，字符串

callbackFun：微信登录用户授权认证回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字,[0,-4,-2]  
> 
> -   0：获取用户信息成功 
>   
> -   其他值：失败
> 
> 
> openId：普通用户的标识，字符串类型，对当前开发者帐号唯一
> 
> nickName：	普通用户昵称，字符串类型
> 
> sex：普通用户性别，数字，1为男性，2为女性
> 
> province：普通用户个人资料填写的省份，字符串类型
> 
> city：普通用户个人资料填写的城市，字符串类型
> 
> country：国家，，字符串类型，如中国为CN
> 
> headImgUrl：	用户头像地址，字符串类型，最后一个数值代表正方形头像大小（有0、46、64、96、132数值可选，0代表640*640正方形头像），用户没有头像时该项为空
> 
> privilege：用户特权信息，json数组，如微信沃卡用户为（chinaunicom） ["PRIVILEGE1", "PRIVILEGE2"]
> 
> unionId：用户统一标识，字符串类型，针对一个微信开放平台帐号下的应用，同一用户的unionid是唯一的。
> 
> errMsg：错误消息值，字符串类型，当code为非0时，有效  

返回值：无

**注：** 关于scope参数相关说明，请参见移动应用微信开发指南相关章节




<span id="ff_6">**isSupportPay(): boolean**</span>  

<code>是否支持微信支付</code>  

参数：无

返回值：boolean型：

> true：支持微信支付
> 
> false：不支持微信支付

**注：** 微信5.0以上版本支持支付功能


<span id="ff_7">**payOrder(jsonData:Object,callBackFun:Function): void**</span>  

<code>调用微信支付订单，并返回授权结果</code>

参数：  

jsonData：Json对象，定义如下：  

> appId：微信开放平台获取的微信应用id，从业务服务器获取，必选项；
> 
> partnerId：商家和微信合作的id号，从业务服务器获取，必选项，；
> 
> orderId：需要支付订单号，字符串类型，从业务服务器获取，必选项；
> 
> nonceStr：随机串，防重发随机串，字符串类型，不超过32个字符，从业务服务器获取，必选项；
> 
> timestamp：防重发,时间戳，字符串类型，商户生成从 1970年 1 月 1 日 00：00：00 至今的秒数，如1412000000，从业务服务器获取，必选项；
> 
> package：订单详情，字符串类型，暂填写固定值Sign=WXPay，必选项；
> 
> sign：商家根据微信开放平台文档对数据做的签名，字符串类型，从业务服务器获取，必选项；

 callbackFun：微信支付获取token值回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> - 0：支付成功
> 
> - 其他值：支付token失败
> 
> errMsg：错误消息描述，字符串类型，当code为非0时有效





<span id="ff_8">**shareText(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享文本到微信好友/微信朋友圈</code>

参数：  

jsonData：Json对象，定义如下：

> type：字符串枚举型,[session，timeline]，可选项，默认session
> 
> - session：分享到微信好友
> 
> - timeline：分享到微信朋友圈
> 
> text：发送的文本内容，字符串类型，必选项，不能为空且小于10K；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> -  0：分享成功
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当code为非0时有效

返回值：无




<span id="ff_9">**shareImage(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享图片到微信好友/微信朋友圈</code>


参数：
jsonData：Json对象，定义如下：

> type：字符串枚举型,[session，timeline]，可选项，默认session
> 
> - session：分享到微信好友
> 
> - timeline：分享到微信朋友圈
> 
> imgPath：只支持本地图片，必选项，本地图片路径，支持res: 及 file: 字符串；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> -  0：分享成功
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无


<span id="ff_10">**shareNews(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享新闻（图文信息）到微信好友/微信朋友圈</code>


参数：
jsonData：Json对象，定义如下：

> type：字符串枚举型,[session，timeline]，可选项，默认session
> 
> - session：分享到微信好友
> 
> - timeline：分享到微信朋友圈
> 
> url：要分享的新闻链接地址，必选项，字符串
> 
> title：要分享的新闻标题，必选项，字符串
> 
> description: 要分享的新闻内容，可选项，字符串
> 
> imgPath：要分享的新闻缩略图url，可选项，支持本地及网络图片；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> -  0：分享成功
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无

**注:** description字段内容不宜过长，否则分享失败，建议在30个左右的字符长度。







