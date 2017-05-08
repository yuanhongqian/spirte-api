# Device 终端设备操作类。

----------

Device终端设备操作类，主要用于控制设备闪光灯，震动，屏幕点亮以及获取设备信息等功能。


使用时需要在js中引入 ：

```javascript
var device = require("Device"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

> **闪光灯** 
> 
>[ startLight(): void  打开移动设备闪光灯 ](#ff_0)
> 
> [ closeLight(): void  关闭移动设备闪光灯 ](#ff_1)
>
> **振动**
>
>[ vibrate(time:number): void  启动移动设备振动  ](#ff_2)
>
>  **屏幕**  
> 
> [setKeepScreenOn(): void  设置应用使用过程中保持屏幕点亮 ](#ff_3)
> 
> [clearKeepScreenOn(): void  清除应用使用过程中保持屏幕点亮  ](#ff_4)
> 
>[ isKeepScreenOn(): boolean  是否设置应用使用过程中保持屏幕点亮  ](#ff_5)
>
> **设备信息**
> 
>[ getEsn(): string  获取设备ESN值  ](#ff_6)
> 
> [getImsi(): string  获取设备IMSI值](#ff_7)
> 
>[ getDeviceToken(): string   获取iOS推送服务器需要的一个代表设备的唯一令牌的字符串](#ff_8)
> 
> [getOs(): string   获取设备操作系统平台](#ff_9)
> 
>[ getPhoneModule(): string  获取手机型号名  ](#ff_10) 
>
>[ getOsVersion(): string  获取设备操作系统版本号](#ff_11)
> 
> [isRoot(): boolean  判断Android设备是否root或iOS设备是否越狱  ](#ff_12)
> 
> [getLanguage(): string  获取当前系统语言类型  ](#ff_13)
> 
> [getAvailableMemory(): number  获取设备可用内存 ](#ff_14) 
> 
> [getDpi(): string  获取当前设备dpi  ](#ff_15)
> 
> **桌面气泡数字**  
> 
> [getBadgeNumber(): number  获取Iphone/Ipad 设备桌面快捷方式小气泡显示数字](#ff_16)
> 
> [setBadgeNumber(number:string): void  设置Iphone/Ipad 设备桌面快捷方式小气泡显示数字  ](#ff_17)



<span id="ff_0">**startLight(): void**</span>  

<code>打开移动设备闪光灯</code>  

参数：  

参数：无   

返回值：无



<span id="ff_1">**closeLight(): void**</span>  

<code>关闭移动设备闪光灯</code>

参数：无   

返回值：无




<span id="ff_2">**vibrate(time:number): void**</span>  

<code>启动移动设备振动</code>   

参数：  

time：振动时长，数字，单位毫秒，可选项；注：仅Android支持，iOS该参数无效  

返回值：无



<span id="ff_3">**setKeepScreenOn(): void**</span>  

<code>设置应用使用过程中保持屏幕点亮</code>  

参数：无   

返回值：无




<span id="ff_4">**clearKeepScreenOn(): void**</span>  

<code>清除应用使用过程中保持屏幕点亮</code> 

参数：无   

返回值：无


<span id="ff_5">**isKeepScreenOn(): boolean**</span>  

<code>是否设置应用使用过程中保持屏幕点亮</code> 

参数：无  

返回值：应用使用过程中保持屏幕点亮，bool型  

> true：设置强制点亮屏幕；
> 
> false：未设置强制点亮屏幕；




<span id="ff_6">**getEsn(): string**</span>  

<code>获取设备ESN值</code>  


参数：无  

返回值：设备ESN值，字符串类型，iOS系统返回内部计算唯一标识


<span id="ff_7">**getImsi(): string**</span>  

<code>获取设备IMSI值</code>   

参数：无  

返回值：设备IMSI值，字符串类型，iOS系统返回内部计算唯一标识


<span id="ff_8">**getDeviceToken(): string**</span>  

<code>获取iOS推送服务器需要的一个代表设备的唯一令牌的字符串</code>  

参数：无  

返回值：iOS设备标识符，字符类型，Android返回null 


<span id="ff_9">**getOs(): string**</span>  

<code>获取设备操作系统平台</code>   

参数：无  

返回值：设备操作系统平台，字符串枚举型，[Android，iOS] 

<span id="ff_10">**getPhoneModule(): string**</span>  

<code>获取手机型号名</code>   

参数：无  

返回值：手机型号名，字符串类型


<span id="ff_11">**getOsVersion(): string**</span>  

<code>获取设备操作系统版本号</code>  

参数：无  

返回值：设备操作系统版本号，字符串类型


<span id="ff_12">**isRoot(): boolean**</span>  

<code>判断Android设备是否root或iOS设备是否越狱</code>   

参数：无  

返回值：设备是否root，bool型


<span id="ff_13">**getLanguage(): string**</span>  

<code>获取当前系统语言类型</code>  

参数：无  

返回值：当前系统语言环境，字符串枚举型，[zh-cn，en-us]  

> zh-cn：中文

> en-us：英文 


<span id="ff_14">**getAvailableMemory(): number**</span>  

<code>获取设备可用内存</code>   

参数：无  

返回值：当前设备可用内存，单位MB，精确到小数点后一位


<span id="ff_15">**getDpi(): string**</span>  

<code>获取当前设备dpi</code>    

返回值：当前设备dpi，字符串枚举型 [ldpi，mdpi，hdpi，xhdpi，xxhdpi]，对应说明如下：

> ldpi：低分屏；
> 
> dpi：中分屏；
> 
> dpi：高分屏；
> 
> hdp：超高分屏；
> 
> xhdpi：超超高分屏


<span id="ff_16">**getBadgeNumber(): number**</span>  

<code>获取Iphone/Ipad 设备桌面快捷方式小气泡显示数字</code>   

参数：无

返回值：返回小气泡显示数字，若无则返回0

<span id="ff_17">**setBadgeNumber(number:string): void**</span>  

<code>设置Iphone/Ipad 设备桌面快捷方式小气泡显示数字</code>   

参数： 

number：显示数字。取值0~999，设置为0则不显示小气泡  

返回值：无

