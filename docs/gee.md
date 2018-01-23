# Gee 极验图形验证码组件

------------

Gee极验图形验证码封装了安全可靠的图形验证码使用场景，由于需要客户端及服务器配合使用，因此使用前需了解其通讯流程，参见：[http://docs.geetest.com/install/overview/#通讯流程](http://docs.geetest.com/install/overview/#通讯流程)。极验证集成说明：[http://docs.geetest.com/install/client/web-front/](http://docs.geetest.com/install/client/web-front/)

Gee为外置组件

<h2 id="cid_1">方法</h2>

本节目录：

>[show(jsonData:Object,callFunction:Function):void 启动极验图片验证码](#ff_0)

<span id="ff_0">**show(jsonData:Object,callFunction:Function):void**</span>

<code>启动极验图片验证码</code>

参数：

jsonData：传递配置信息，json格式，定义如下：

> gt：验证id的参数，字符串数据，从服务器获取；
> 
> challenge：验证质询/流水号参数，字符串数据，从服务器获取；
> 
> success：宕机状态，bool型，从服务器获取
> 
> https：是否启用https，bool型，非必选项，true：启动https，付费用户使用；false：不启用https（默认）
> 
> language：校验语言，字符串枚举型，非必选项。【zh-cn，zh-hk，zh-tw，ko-kr，ja-jp，en-us】，默认zh-ch简体中文；

callFunction：回调函数，入参为json类型，定义如下：

> code：状态码，数字【0，-1，-2】，0：校验成功；-1：取消校验；-2：其他错误；
> 
> challenge：校验成功返回challenge参数，字符串类型，用于二次校验使用；
> 
> validate：校验成功返回validate参数，字符串类型，用于二次校验使用；
> 
> seccode：校验成功返回seccode参数，字符串类型，用于二次校验使用；

返回值：无

注：使用极验详细流程请参考：
[http://www.geetest.com/install/sections/idx-client-sdk.html](http://www.geetest.com/install/sections/idx-client-sdk.html)

