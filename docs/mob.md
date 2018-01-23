# Mob 免费短信工具类

--------

Mob平台提供了免费短信&语音验证码SDK，可以实现短信&语音验证功能。Mob最大的特点是应用再该平台申请通过后每天1万免费额度，适合刚起步的应用。使用前需到mob.com注册账号获得appKey和secretKey。Mob短信验证码流程：[http://wiki.mob.com/smssdk-web-1-3-0verify/](http://wiki.mob.com/smssdk-web-1-3-0verify/)

Mob免费短信&语音验证码类，外置组件

<h2 id="cid_1">方法</h2>

本节目录：

> [sendSmsAsyn(jsonData:Object,callbackFun:Function):void 后台发送短信](#ff_0)
> 
> [sendSms(jsonData:Object,callbackFun:Function):void 发送短信验证码](#ff_1)
> 
> [sendVoice(jsonData:Object,callbackFun:Function):void 发送语音验证码](#ff_2)
> [verifyCode(jsonData:Object,callbackFun:Function):void 向服务器发送验证码，获取验证结果](#ff_3)


<span id="ff_0">**sendSmsAsyn(jsonData:Object,callbackFun:Function):void**</span>

<code>后台发送短信</code>

参数：

jsonData：短信发送传递参数，json类型，必选项，定义如下：

> phone：需要发送的手机号码，字符串类型，必选项
> content：需要发送内容，字符串类型，必选项

callbackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】。0：发送短信成功；-1：发送短信失败；

返回值：无

注：仅Android支持


<span id="ff_1">**sendSms(jsonData:Object,callbackFun:Function):void**</span>

<code>发送短信验证码</code>

参数：

jsonData：短信发送传递参数，json类型，必选项，定义如下：

> phone：需要验证的手机号，字符串类型，必选项

callbackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：发送短信验证码成功；-1：发送短信验证码失败；

返回值：无

**注：**

1：请求sendSms的时间间隔不应该小于60秒，否则服务端会返回“操作过于频繁”的错误；

2：一般而言短信验证码5秒内可以到达，但部分短信会有延迟，最好提示下用户


<span id="ff_2">**sendVoice(jsonData:Object,callbackFun:Function):void**</span>

<code>发送语音验证码</code>

参数：

jsonData：短信发送传递参数，json类型，必选项，定义如下：

> phone：需要验证的手机号，字符串类型，必选项

callbackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：发送语音验证码成功；-1：发送语音验证码失败；

返回值：无

注：请求sendVoice的时间间隔不应该小于60秒，否则服务端会返回“操作过于频繁”的错


<span id="ff_3">**verifyCode(jsonData:Object,callbackFun:Function):void**</span>

<code>向服务器发送验证码，获取验证结果</code>

参数：

jsonData：向服务器发送验证码参数，json格式，定义如下：

> phone：需要验证的手机号，字符串类型，必选项
> 
> code：用户输入的验证码，字符串类型，必选项

callbackFun：回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：验证码校验成功；-1：验证码校验失败

返回值：无

