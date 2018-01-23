# Barcode 条码/二维码扫描操作类

----------



使用时需要在js中引入 ：

```javascript
var barcode = require("Barcode"); 
```

**注：** 该组件为外置功能组件，打包需要选择此功能。

<h2 id="cid_1">js方法</h2>  


本节目录：

>[ scan(jsonData:Object,callBackFun:Function): void  启动条码扫描 ](#ff_0)
> 
> [decodeImage(jsonData:Object,callBackFun:Function): void  传入图片路径进行二维码扫码 ](#ff_1)
>
>[ createImage(jsonData:Object,callBackFun:Function): void   根据传入字符串生成条码编码图片并保存  ](#ff_2)

<span id="ff_0">**scan(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动条码扫描</code>    

参数：  

jsonData：Json对象，定义如下：  

> type：启动扫码类型，字符串枚举型[0,1,2]，必选参数
> 
> - 0：单次扫码
> 
> - 1：多次扫码，一次返回扫码结果
> 
> - 2：多次扫码每均返回扫码结果
> 
> photo：扫码界面是否支持相册选择，字符串枚举型[0,1]，默认0，可选参数。
> 
> - 0：不支持相册选择；
> 
> - 1：支持相册选择；
> 
> mode：默认扫码模式，字符串枚举型[0, 1]，可选参数
> 
> -  0：二维码，扫码取景框为正方形（默认）；
> 
> -  1：条形码，扫码取景框为长条形。

callbackFun：扫码回调函数，入参为Json对象，定义如下：

> **单次扫码：**
> 
> code：回应状态码，数字[0,-1]
> 
> - 0：扫码成功；
> 
> - -1：用户取消扫码
> 
> result：扫码结果，字符串，扫码成功有效
> 
> codeType：条码类别，字符串，扫码成功有效
 
> **多次扫码，一次返回所有扫码结果**
> 
> code：回应状态码，数字[0,-1]
> 
> - 0：扫码成功；
> 
> - -1：用户取消扫码或扫码未成功点击确定
> 
> results：扫码结果，json数组，扫码成功有效，数组项json字段，定义如下：
> 
> - result：扫码结果，字符串，扫码成功有效
> 
> - codeType：条码类别，字符串，扫码成功有效
 
> **多次扫码，每次均返回扫码结果**
> 
> code ：回应状态码，数字[0,-1]
> 
> - 0：扫码成功；
> 
> - -1：用户取消扫码或扫码未成功点击确定
> 
> result：扫码结果，字符串，扫码成功有效
> 
> codeType：条码类别，字符串，扫码成功有效




示例：

```javascript
var barcode = require("Barcode"); 
var jsonData = {};
jsonData.type = 0;
jsonData.photo = 1;
jsonData.mode = 0;
barcode.scan(jsonData,function(json){
	var smcoee = json.code;
	var smresult = json.result;
	var smcodetype = json.codeType;
});
```




<span id="ff_1">**decodeImage(jsonData:Object,callBackFun:Function): void**</span>  

<code>传入图片路径进行二维码扫码</code>


参数：

jsonData：Json对象，定义如下：

> path：传入二维码图片路径，支持res: file:前缀路径传入。
> 
> callBackFun：回调函数，入参为Json对象，定义如下：
> 
> code：回应状态码，数字[0,-1]
> 
> - 0：扫码成功；
> 
> - -1：扫描失败
> 
> result：扫码结果，字符串，扫码成功有效
> 
> codeType：二维码类别，字符串，扫码成功有效


<span id="ff_2">**createImage(jsonData:Object,callBackFun:Function): void**</span>  

<code>根据传入字符串生成条码编码图片并保存</code>  

生成条码图片格式为png

参数：  

jsonData：生成条码参数，Json对象，定义如下：  

> content：需要进行编码的内容，字符串，必选项；
> 
> format：生成条码格式，字符串枚举[CODE_39,CODE_128,EAN_8,EAN_13]必选项；
> 
> savePath：生成条码图片保存路径，res: file：前缀路径，字符串类型，必选项；
> 
> width：需要生成图片的宽度，数字，单位px，必选项；
> 
> height：需生成图片的高度，数字，单位px，必选项；

callBackFun：结果回调函数，入参为Json对象，定义如下：  

> code：回应状态码，数字[0,-1]
> 
> - 0：条码图生成成功；
> 
> - -1：条码图生成失败；
> 
> savePath：生成条码图片保存路径，res: file：前缀路径，字符串类型；
