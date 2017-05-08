# ImageUtil 图片处理工具类

----------

 ImageUtil 图片处理工具类，用于开发者对图片自定义处理。

使用时需要在js中引入 ：

```javascript
var imageutil = require("ImageUtil"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ scale(jsonData:Object,callBackFun:Function): void   缩放图片并保存到目标文件 ](#ff_0)
> 
> [scaleByRate(jsonData:Object,callBackFun:Function): void  根据缩放比例缩放图片并保存到目标文件 ](#ff_1)
> 
> [scaleByFileSize (jsonData:Object,callBackFun:Function): void   根据缩放后文件大小缩放图片并保存到目标文件 ](#ff_2)
> 
> [clip(jsonData:Object,callBackFun:Function): void    启动图片裁剪界面 ](#ff_3)
> 
> [screenShot(jsonData:Object,callFunction:Function): void  启动截屏](#ff_4)


<span id="ff_0">**scale(jsonData:Object,callBackFun:Function): void**</span>  

<code>缩放图片并保存到目标文件</code>  

缩放图片并保存到目标文件，结果通过回调函数返回   

参数：  

jsonData，缩放传递参数，Json对象，定义如下：  

> source：需要裁剪原图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> target：生成压缩后图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> width：缩放后图片的宽度，单位像素，缩放后图片高度等比缩放，数字，可选项；
> 
> compress：图片压缩后质量比，数字类型，取值[1~100]，若不设置则默认100质量不压缩，可选项，注：对png格式图片无效；

callBackFun，结果回调函数，函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字[0,-1]
> 
> -  0：压缩图片成功；
> 
> -  -1：压缩图片失败；
> 
> source：需要转换原图片路径，字符串类型；
> 
> target：生成压缩后图片路径，字符串类型；
> 
> width：缩放后图片的宽度，单位像素，数字类型
> 
> compress：图片压缩后质量比，数字类型，取值[1~100]；

返回值：无



<span id="ff_1">**scaleByRate(jsonData:Object,callBackFun:Function): void**</span>

<code>根据缩放比例缩放图片并保存到目标</code>    

参数：

jsonData，缩放传递参数，Json对象，定义如下：  

> source：需要转换原图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> target：生成压缩后图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> rate：图片尺寸缩放比例，数字类型，取值[0-1]，必选项。

callBackFun，结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：压缩图片成功；
> 
> - -1：压缩图片失败；
> 
> source：需要转换原图片路径，字符串类型；
> 
> target：生成压缩后图片路径，字符串类型；
> 
> rate：图片尺寸缩放比例，数字类型，取值[0-1] 

返回值：无






<span id="ff_2">**scaleByFileSize (jsonData:Object,callBackFun:Function): void**</span>  

<code>根据缩放后文件大小缩放图片并保存到目标文件</code>   

参数：

jsonData，缩放传递参数，Json对象，定义如下：  

> source：需要转换原图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> target：生成压缩后图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> size：压缩后图片尺寸，数字类型，单位kb，实际的尺寸不会很准确，可能略大于或略小于目标尺寸，必选项。

callBackFun，结果回调函数，函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字[0,-1]
> 
> - 0：压缩图片成功；
> 
> - -1：压缩图片失败；
> 
> source：需要转换原图片路径，字符串类型；
> 
> target：生成压缩后图片路径，字符串类型；
> 
> size：压缩后图片尺寸，数字类型，单位kb；

返回值：无



<span id="ff_3">**clip(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动图片裁剪界面</code> 

参数： 

jsonData，图片裁剪传递参数，Json对象，定义如下：

> source：需要裁剪图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> target：裁剪后图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> cropWidth：裁剪图片宽度，数字类型，单位px，必选项；

callBackFun，结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：裁剪图片成功；
> 
> - -1：裁剪图片失败；
> 
> source：需要裁剪图片路径，字符串类型；
> 
> target：裁剪后图片路径，字符串类型；

返回值：无


<span id="ff_4">**screenShot(jsonData:Object,callFunction:Function): void**</span>  

<code>启动截屏</code>  


参数： 

jsonData：截屏参数，json类型，必选项，定义如下：

> path：截屏后图片保存路径，支持res:，file:前缀的本地路径，图片为jpg格式，字符串类型，必选项；
> 
> isAlbum：截屏后图片是否保存至系统相册，bool型，可选项，默认不保存相册

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：截屏成功；
> 
> - -1：截屏失败；

返回值：无 

**注：** Android部分机型会存在保存至相册后，通过系统的相册APP无法查看问题

