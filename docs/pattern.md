# Pattern 为九宫手势锁屏功能组件

----------

Pattern为九宫手势锁屏功能组件，提供手势密码相关操作，包括：启动手势密码锁；关闭手势密码锁；获取是否开启手势密码；获取是否已成功设置手势；获取/设置手势重复输入校验次数；获取/设置最短设置密码长度；获取/设置手势密码生效时间；获取/设置忘记密码跳转url；启动打开手势锁屏界面；启动打开手势设置界面等
    注：该组件为外置组件



使用时需要在js中引入 ：

```javascript
var pattern = require("Pattern"); 
```

**注：** 该组件为外置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：


> 
>[ enablePattern():void   设置启动手势密码锁 ](#ff_0)
> 
> [disablePattern():void 设置关闭手势密码锁 ](#ff_1)
>
> [isPattern():boolean   是否开启手势密码锁  ](#ff_2)
> 
> [isSetPatternPassword():boolean   是否已设置成功手势密码](#ff_3)
> 
> [setPatternTimeout(time:number):void    设置手势密码锁生效时间](#ff_4)
> 
> [getPatternTimeout():number  获取手势密码锁生效时间 ](#ff_5)
> 
> [setPatternForgetUrl(url:string):void  设置忘记密码跳转url](#ff_6)
> 
> [setPatternStyle(jsonData:object):void   设置手势锁屏界面/设置界面样式](#ff_7)
> 
> 
> [getPatternStyle():object   返回设置的手势锁屏界面/设置界面样式 ](#ff_8)
> 
> 
> [openSetPattern(resultCallback:Function) :void   启动设置手势密码界面](#ff_9)
> 
> 
> [openPattern(successCallback:Function):void   打开手势锁屏界面 ](#ff_10)
> 
> [getPatternMinLength():number   获取最短设置密码长度,默认最短4位](#ff_11)
> 
> [setPatternMinLength ( num:number):boolean   设置最短设置密码长度 ](#ff_12)
> 
> 
> [getPatternCheckNumber():number   获取重复输入校验次数](#ff_13)
> 
> 
> [setPatternCheckNumber(num:number):boolean  设置重复输入校验次数](#ff_14)
> 
> 
> [getPatternPassword():string  获取当前应用插件设置的手势密码 ](#ff_15)
> 
> 
> [setPatternPassword (password:string):boolean  设置当前应用插件设置的手势密码](#ff_16)
> 
> 
> [setPatternLogo(logoPath:string):void  设置九宫手势密码锁屏界面logo图](#ff_17) 
> 
> [setPatternPrompt(prompt:string):void   设置九宫手势密码锁屏界面提示语](#ff_18)


<span id="ff_0">**enablePattern():void**</span>  

<code>设置启动手势密码锁</code>  

参数：无  

返回值：无  

<span id="ff_1">**disablePattern():void**</span>  

<code>设置关闭手势密码锁</code>

参数：无  

返回值：无


<span id="ff_2">**isPattern():boolean**</span>  

<code>是否开启手势密码锁</code>

参数：无 

返回值：bool型

> true：开启
> 
> false：关闭

<span id="ff_3">**isSetPatternPassword():boolean**</span>  

<code>是否已设置成功手势密码</code>  

参数：无  

返回值：bool型

> true：开启
> 
> false：关闭


<span id="ff_4">**setPatternTimeout(time:number) :void**</span>  

<code>设置手势密码锁生效时间</code>    

默认5分钟 

参数：

time：超时时间，单位：分钟，float型，必选项

返回值：无

**注：** 超时时间范围为[0,30]，Android系统若设置为0，切换至后台需要等待2~3s后锁屏界面方可生效。


<span id="ff_5">**getPatternTimeout():number**</span>  

<code>获取手势密码锁生效时间</code> 

参数: 无

返回值：

已设置手势密码锁超时时间，float型，单位分钟  


<span id="ff_6">**setPatternForgetUrl(url:string):void	**</span>  

<code>设置忘记密码跳转url</code> 

参数：

url：忘记密码跳转页，支持res：前缀本地页面，字符串类型

**注：**

若用户未设置该url或该url页面未找到，则用户在锁屏页面点击忘记密码或者输入次数超出次数执行重新进入应用操作  

<span id="ff_7">**setPatternStyle(jsonData:object):void	**</span>  

<code>设置手势锁屏界面/设置界面样式</code>

参数：

jsonData：需要设置的样式，json格式，均为可选项，定义如下：

**通用：**

> cellIcon：九宫格cell图，字符串类型，支持res：前缀本地图片
> 
> cellSelectedIcon：九宫格cell选中图，字符串类型，支持res：前缀本地图片
> 
> cellErrorIcon：九宫格cell错误图，字符串类型，支持res：前缀本地图片
> 
> lineColor：绘制线颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb），默认#0a7fff
> 
>  lineErrorColor：错误绘制线颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb），,默认#ff0000
>  
> lineSize：绘制线宽度，数字类型，默认10
> 
> tipColor：文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）,默认#000000
> 
> tipErrorColor：错误状态下文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）,默认#ff0000

**设置界面:**

> settingTitleBgColor：设置锁屏界面标题栏背景色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）,默认#f9f9f9
> 
> settingTitleColor：设置锁屏界面标题栏文字色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）,默认#565656
> 
> settingTitleIcon：设置锁屏界面标题栏返回按钮图片，字符串类型，支持res：前缀本地图片
> 
> settingTitleClickIcon：设置锁屏界面标题栏点击返回按钮图片，字符串类型，支持res：前缀本地图片
> 
> settingBgImage：设置锁屏界面背景图，字符串类型，支持res：前缀本地图片

**锁屏界面:**

> forgetColor："忘记手势密码" 文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）,默认#0a7fff
> 
> bgImage：锁屏界面背景图，字符串类型，支持res：前缀本地图片

返回值：无  


<span id="ff_8">**getPatternStyle():object**</span>  

<code>返回设置的手势锁屏界面/设置界面样式</code> 

参数：

jsonData：已设置的样式，json格式，定义如下：

**通用：**

> cellIcon：九宫格cell图，字符串类型，支持res：前缀本地图片
> 
> cellSelectedIcon：九宫格cell选中图，字符串类型，支持res：前缀本地图片
> 
> cellErrorIcon：九宫格cell错误图，字符串类型，支持res：前缀本地图片
> 
> lineColor：绘制线颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）
> 
>  lineErrorColor：错误绘制线颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）
>  
> lineSize：绘制线宽度，数字类型
> 
> tipColor：文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）
> 
> tipErrorColor：错误状态下文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）

**设置界面:** 

> settingTitleBgColor：设置锁屏界面标题栏背景色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）
> 
> settingTitleColor：设置锁屏界面标题栏文字色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）     settingTitleIcon：设置锁屏界面标题栏返回按钮图片，字符串类型，支持res：前缀本地图片
> 
> settingTitleClickIcon：设置锁屏界面标题栏点击返回按钮图片，字符串类型，支持res：前缀本地图片
> 
> settingBgImage：设置锁屏界面背景图，字符串类型，支持res：前缀本地图片

**锁屏界面: **

> forgetColor："忘记手势密码" 文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）
> 
> bgImage：锁屏界面背景图，字符串类型，支持res：前缀本地图片
> 

**注：** 若未通过setPatternStyle设置则返回null




<span id="ff_9">**openSetPattern(resultCallback:Function) :void**</span>  

<code>启动设置手势密码界面</code> 

参数： 

resultCallback：回调函数，必选项，该回调函数参数为Json格式，定义如下：
> 
>  code：操作结果，数字枚举型，【0，-1】，0：设置成功；-1：设置失败
>  
返回值：无  

**注： **

> 1：若用户未设置启动手势密码锁，则即使触发该函数手势设置界面也不弹出；
> 
> 2：默认密码设置最少长度为4；  


<span id="ff_10">**openPattern(successCallback:Function):void**</span>  

<code>打开手势锁屏界面</code>  

参数： 

successCallback：手势解锁成功回调函数  可选项 

返回值：无 

注：
> 1：若用户未设置启动手势密码锁或未成功设置手势密码，则即使触发该函数手势锁屏界面将不弹出；
> 
> 2：锁屏界面尝试次数内若无法争取解锁或点击锁屏界面下方放置忘记密码项，关闭密码界面及所有打开应用界面，进入适配开发人员设置的指定页面；
> 
> 3：默认重复校验次数为5；

<span id="ff_11">**getPatternMinLength():number**</span>  

<code>获取最短设置密码长度</code>  

默认最短4位 

参数：无 

返回值: 最短密码长度int型


<span id="ff_12">**setPatternMinLength ( num:number):boolean**</span>  

<code>设置最短设置密码长度</code>  

若不设置则默认4位 

参数： 

> num：需设置最短密码长度，int型

返回值：bool型, true：设置成功, false：设置失败  

<span id="ff_13">**getPatternCheckNumber():number**</span>  

<code>获取重复输入校验次数</code>   

默认5次

参数：无  

返回值: 校验次数int型


<span id="ff_14">**setPatternCheckNumber(num:number):boolean**</span>  

<code>设置重复输入校验次数</code>   

若不设置则默认5次 

参数： 
> 
> num：校验次数，int型 

返回值：bool型,rue：设置成功,false：设置失败


<span id="ff_15">**getPatternPassword():string**</span>  

<code>获取当前应用插件设置的手势密码</code>    

参数：无 

返回值：设置手势密码值，字符串类型，如: “12369”，若未设置则返回null


<span id="ff_16">**setPatternPassword (password:string):boolean**</span>  

<code>设置当前应用插件设置的手势密码</code>  

参数： 

password：需要设置的手势密码值，字符串类型，如: "123469"

返回值：boolean型，true：设置手势密码成功；false：设置手势密码失败


<span id="ff_17">**setPatternLogo(logoPath:string):void**</span>  

<code>设置九宫手势密码锁屏界面logo图</code>  

参数： 

> logoPath：需设置logo图路径，字符串类型，支持res:前缀本地图片,必选项，默认不设置logo图。

返回值：无


<span id="ff_18">**setPatternPrompt(prompt:string):void**</span>  

<code>设置九宫手势密码锁屏界面提示语</code> 

参数： 
> 
> prompt：需设置提示语，字符串类型。默认提示语为”请输入手势密码” 

返回值：无










