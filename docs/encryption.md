# Encryption 字符串编解码类

----------

Encryption字符串编解码类，主要用于处理各种字符串编码，如base64，md5，sha，urlEncode等编码。


使用时需要在js中引入 ：

```javascript
var encryption = require("Encryption"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ base64Encode(src:string): string  对传入的src字符串进行base64编码 ](#ff_0)
> 
> [ base64Decode(src:string): string  对传入的src字符串进行base64解码 ](#ff_1)
>
>[ uuid(): string   生成唯一UUID字符串  ](#ff_2)
>
> [md5(src:string): string  对传入的src字符串进行md5加密 ](#ff_3)
> 
> [sha(src:string,type:string): string   对传入的src字符串进行hash编码  ](#ff_4)
> 
>[ urlEncode(src:string,type:string): string   对传入的src字符串进行UrlEncode  ](#ff_5)
>
>[ escapeXml(str:string): string  转换xml中需要转义的字符  ](#ff_6)
>
>[ unEscapeXml(str:string): string  逆转xml中转义符  ](#ff_7)
>
>[ rgbToHex(rgbJson:Object): string  将rgb格式转换为#rrggbb格式字符串  ](#ff_8)
>
>[ hexToRgb(hex:string): Object   将#rrggbb格式字符串转换为rgb格式  ](#ff_9)
> 
> [rgbaToHex(rgba:string): string   将rgba格式字符串转换为#aarrggbb  ](#ff_10)
> 
> [hexToRgba(hex:string): Object  将#aarrggbb格式字符串转换为rgba](#ff_11)  





<span id="ff_0">**base64Encode(src:string): string **</span>  

<code>对传入的src字符串进行base64编码</code>  

参数：  

src：需要进行编码的字符串，字符串类型  

返回值：返回编码后字符串数据，字符串类型



<span id="ff_1">**base64Decode(src:string): string**</span>  

<code>对传入的src字符串进行base64解码</code>

参数：  

src：需要base64解码的字符串，字符串类型  

返回值：返回解码后字符串数据



<span id="ff_2">**uuid(): string**</span>  

<code>生成唯一UUID字符串</code>   

参数：无  

返回值：唯一UUID字符串，字符串类型，字母小写






<span id="ff_3">**md5(src:string): string**</span>  

<code>对传入的src字符串进行md5加密</code>  

参数：  

src：需要Md5加密的字符串，字符串类型  

返回值：返回Md5加密后字符串数据，字母小写



<span id="ff_4">**sha(src:string,type:string): string**</span>  

<code>对传入的src字符串进行hash编码</code> 


参数：  

src：需要hash编码的字符串，字符串类型  

type：hash加密类型，字符串枚举型，[SHA1,SHA224,SHA256,SHA384,SHA512]，可选项，默认为SHA1加密

返回值：返回sha加密后后字符串数据



<span id="ff_5">**urlEncode(src:string,type:string): string**</span>  

<code>对传入的src字符串进行UrlEncode编码</code> 

参数：  

src：需要进行编码的字符串，字符串类型  

type：编码类型，数字，取值为[ 0, 1 ]，默认为0。

> 0：gb2312编码；
> 
> 1：utf-8 编码  

返回值：返回urlEncode编码后字符串数据


<span id="ff_6">**escapeXml(str:string): string**</span>  

<code>转换xml中需要转义的字符</code>   

转换xml中需要转义的字符，包括：[<，>，&，'，"]

参数：  

str：包含转义字符的字符串，字符串类型   

返回值：转换后的得到的字符串，字符串类型

> &lt; 转换后&amp;lt;
> 
> &gt; 转换后&amp;gt;
> 
> &amp;转换后&amp;amp;
> 
> &apos; 转换后&amp;apos;
> 
> &quot; 转换后 &amp;quot;


<span id="ff_7">**unEscapeXml(str:string): string**</span>  

<code>逆转xml中转义符</code>   


逆转xml中转义符，包括：[&amp;lt;，&amp;gt;，&amp;amp;，&amp;apos;，&amp;quot;]  

参数：  

str：包含转义后字符的字符串，字符串类型   

返回值：逆转后的得到的字符串，字符串类型  

> &amp;lt;转换后<
> 
> &amp;gt;转换后 >
> 
> &amp;amp; 转换后 &
> 
> &amp;apos; 转换后 '
> 
> &amp;quot; 转换后 "


<span id="ff_8">**rgbToHex(rgbJson:Object): string**</span>  

<code>将rgb格式转换为#rrggbb格式字符串</code>    

参数：  

rgb：待转换的rgb数据，Json对象，定义如下：

> red：red色值，数字，0-255；
> green：green色值，数字，0-255；
> blue：blue色值，数字，0-255；

返回值：转换后#rrggbb格式字符串，如：#ff0000


<span id="ff_9">**hexToRgb(hex:string): Object**</span>  

<code>将#rrggbb格式字符串转换为rgb格式</code>  

参数： 

hex：待转换的#rrggbb格式字符串，字符串类型，如：#ff0000  

返回值：转换后rgb数据，Json对象，定义如下：  

> red：red色值，数字，0-255；
> 
> green：green色值，数字，0-255；
> 
> blue：blue色值，数字，0-255；


<span id="ff_10">**rgbaToHex(rgba:string): string**</span>  

<code>将rgba格式字符串转换为#aarrggbb</code>   

参数：  

rgba：待转换的rgba数据，Json对象，定义如下：  

> red：red色值，数字，0-255；
> 
> green：green色值，数字，0-255；
> 
> blue：blue色值，数字，0-255；
> 
> alpha：alpha透明度，数字，0-1
   
返回值：转换后#aarrggbb格式字符串，如：#ccff0000


<span id="ff_11">**hexToRgba(hex:string): Object**</span>  

<code>将#aarrggbb格式字符串转换为rgba</code>   

参数：  

hex：待转换的#aarrggbb格式字符串，字符串类型，如：#ccff0000  

返回值：转换后的rgba数据，Json对象，定义如下：  

> red：red色值，数字，0-255；
> 
> green：green色值，数字，0-255；
> 
> blue：blue色值，数字，0-255；
> 
> alpha：alpha透明度，数字，0-1
