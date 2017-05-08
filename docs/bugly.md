#  腾讯Bugly类

----------

腾讯Bugly类，为移动开发者提供专业的异常崩溃日志上报，，帮助开发者快速发现并解决异常，开发人员需要主动至腾讯Bugly平台注册应用相关信息：[https://bugly.qq.com/v2/](https://bugly.qq.com/v2/)

使用时需要在js中引入 ：

```javascript
var bugly = require("Bugly"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

> **异常上报**
> 
> [init(jsonData:Object): void  启动Bugly错误日志收集](#ff_0)
> 
> [setUserId(userId:string): void  设置用户Id，用于精确定位到应用中某个用户异常 ](#ff_1)
> 
> [getUserId(): string  获取用户Id ](#ff_2)
> 
> [setTag(tag:number): void  设置自定义标签](#ff_3)
> 
> [getTag(): number   获取当前设置标签值](#ff_4)
> 
> [setUserData(jsonData:Object): void  设置自定义Map参数](#ff_5)
> 
> [getUserData(key:string): string  获取已设置自定义Map参数](#ff_6)
> 
> [getSdkVersion(): string  获取Bugly SDK版本号](#ff_7)
> 
> [getDeviceId(): string  获取设备Id](#ff_8)
> 
> 
> **自定义日志**
> 
> [verbose(log:string): void  Bugly基础日志输出](#ff_9)
> 
> [debug(log:string): void  Bugly调试日志输出](#ff_10)
> 
> [info(log:string): void  Bugly信息日志输出](#ff_11)
> 
> [warn(log:string): void  Bugly告警日志输出  ](#ff_12)
> 
> [error(log:string): void  Bugly错误日志输出](#ff_13)



<span id="ff_0">**init(jsonData:Object): void**</span>  

<code>启动Bugly错误日志收集</code>  

参数：  

jsonData，Bugly参数设置，Json类型，定义如下：  

> appId：应用标识，字符串类型，必选项；
> 
> appVersion：应用版本号，字符串类型，可选项；
> 
> appChannel：应用渠道号，字符串类型，可选项；
> 
> appPackageName：应用包名，字符串类型，可选项，仅Android支持；
> 
> isDebug：是否开启调试模式，bool型，可选项
> 
> - true：开启调试模式
> 
> - false：关闭调试模式（默认）

**注：** 该方法建议放置于应用启动入口js中


<span id="ff_1">**setUserId(userId:string): void**</span>  

<code>设置用户Id</code>  

设置用户Id，用于精确定位到应用中某个用户异常

参数：  

userId：应用系统中用户Id，字符串类型，必选项；  

返回值：无



<span id="ff_2">**getUserId(): string**</span>  

<code>获取用户Id</code>  

参数：无

返回值：获取用户Id，字符串类型，未设置则返回null



<span id="ff_3">**setTag(tag:number): void**</span>  

<code>设置自定义标签</code> 

设置自定义标签，用于标明应用的某个场景，以最后设置的标签值为准

参数：  

tag：自定义标签值，在Bugly标签管理中配置生成，数字类型，必选项；  

返回值：无 


<span id="ff_4">**getTag(): number**</span>  

<code>获取当前设置标签值</code>  

参数：无  

返回值：当前设置标签值，数字类型

<span id="ff_5">**setUserData(jsonData:Object): void**</span>  

<code>设置自定义Map参数</code>

参数： 

jsonData：需设置的自定义key-value参数，随崩溃日志产生时上报，Json对象，value值为字符串类型

返回值：无

**注：** 最多可以有9对自定义的key-value（超过则添加失败），key限长50字节、value限长200字节，过长截断 


<span id="ff_6">**getUserData(key:string): string**</span>  

<code>获取已设置自定义Map参数</code>

参数：

key：需获取自定义数据key值，字符串类型，必选项

返回值：自定义数据value值，字符串类型 


<span id="ff_7">**getSdkVersion(): string**</span>  

<code>获取Bugly SDK版本号</code>

参数：无  

返回值：Bugly SDK版本号，字符串类型

<span id="ff_8">**getDeviceId (): string**</span>  

<code>获取设备Id</code>

参数：无 

返回值：设备Id，字符串类型

**注：** 仅iOS支持

<span id="ff_9">**verbose(log:string): void**</span>  

<code>Bugly基础日志输出</code>

参数： 

log：需要输出日志，字符串类型，必选项 

返回值：无


<span id="ff_10">**debug(log:string): void**</span>  

<code>Bugly调试日志输出</code>

参数： 

log：需要输出日志，字符串类型，必选项

返回值：无



<span id="ff_11">**info(log:string): void**</span>  

<code>Bugly信息日志输出</code>

参数：

log：需要输出字符串，字符串类型，必选项

返回值：无


<span id="ff_12">**warn(log:string): void**</span>  

<code>Bugly告警日志输出</code>

参数： 

log：需要输出字符串，字符串类型，必选项

返回值：无


<span id="ff_13">**error(log:string): void**</span>  

<code>Bugly错误日志输出</code>

参数：

log：需要输出日志，字符串类型，必选项

返回值：无
