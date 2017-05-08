# Pixel 设备的像素访问类

----------

Pixel设备的像素访问类，提供获取设备像素密度，px与dp转换方法。

使用时需要在js中引入 ：

```javascript
var pixel = require("Pixel"); 
```

**注：** 该组件为内置功能组件

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ getDensity(): number  获取设备屏幕密度 ](#ff_0)
> 
> [px2dp(pxValue:number): number  将绝对像素px转换为相对像素dp ](#ff_1)
>
>[ dp2px(dpValue:number): number  将相对像素dp转换为绝对像素px  ](#ff_2)


<span id="ff_0">**getDensity(): number**</span>  

<code>获取设备屏幕密度</code>     

参数：无

返回值：设备屏幕密度，如：  

> 1：mdpi Android 设备 (160 dpi) ；
> 
> 1.5：hdpi Android 设备 (240 dpi) ；
> 
> 2：iPhone 4, 4S，iPhone 5, 5c, 5s，iPhone 6及xhdpi Android 设备 (320 dpi)；
> 
> 3：iPhone 6 plus及xxhdpi Android 设备 (480 dpi)等；
> 
> 3.5：Nexus 6等；


<span id="ff_1">**px2dp(pxValue:number): number**</span>  

<code>将绝对像素px转换为相对像素dp</code>   

参数： 

pxValue：待转换绝对像素，单位px，数字类型

返回值：转换后的相对像素，单位dp，数字类型


<span id="ff_2">**dp2px(dpValue:number): number**</span>  

<code>将相对像素dp转换为绝对像素px</code>  

参数：  

dpValue：待转换相对像素，单位dp，数字类型  

返回值：转换后的绝对像素，单位px，数字类型