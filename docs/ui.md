# UI 界面相关操作类

----------

UI界面相关操作类，包括：alert，toast，confirm，selectFile，selectImage，selectTime，selectDate等。。


使用时需要在js中引入 ：

```javascript
var ui = require("UI"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ alert(jsonData:Object,callFunction:Function): void  弹出提示框 ](#ff_0)
> 
> [confirm(jsonData:Object,callFunction:Function): void  弹出提示选择框 ](#ff_1)
>
>[ toast(jsonData:Object): void   弹出Toast提示  ](#ff_2)
>
> [actionSheet(jsonData:Object,callFunction:Function): void 弹出底部菜单选择 ](#ff_3)
> 
>[selectDate(jsonData:Object,callFunction:Function): void  弹出系统日期选择 ](#ff_4)
> 
> [selectTime(jsonData:Object,callFunction:Function): void   弹出系统时间选择 ](#ff_5)
>
>[ showImages(jsonData:Object): void   显示图片集  ](#ff_6)
>
> [selectFile(jsonData:Object,callBackFun:Function): void    通过js实现文件选择器调用 ](#ff_7)
>
>[ selectVideo(jsonData:Object,callBackFun:Function): void   选择设备中单个视频 ](#ff_8)
> 
> [selectImage(jsonData:Object,callBackFun:Function): void  选择设备中单张图片 ](#ff_9)
>
>[ selectImages(jsonData:Object,callBackFun:Function): void  选择设备中多张图片  ](#ff_10)



<span id="ff_0">**alert(jsonData:Object,callFunction:Function): void**</span>  

<code>弹出提示框</code>    

参数：  

jsonData：弹出提示框传入参数，Json对象，定义如下：  

>    title：标题，字符串类型，可选项,默认显示"提示"；
>    
>    content：内容，字符串类型，必选项；
>    
>    buttonText：按钮文字，字符串类型，可选项，默认显示"确定"；

callFunction：点击触发回调函数，可选参数  

返回值：无


**注：**  系统的alert弹出框，不同手机UI效果可有差异。




<span id="ff_1">**confirm(jsonData:Object,callFunction:Function): void**</span>  

<code>弹出选择提示框</code>

参数：  

jsonData：弹出提示框传入参数，Json对象，定义如下：  

>    title：标题，字符串类型，可选项，默认显示"提示"；
>    
>    content：内容，字符串类型，必选项；
>    
>    buttonTexts：按钮文字数组，数组类型，可选项，若不设置则默认两个按钮，"确定"，"取消"；

callFunction：点击触发回调函数，入参为数字，标识点击索引，取值范围[0-按钮数组size)，可选参数

返回值：无

**注：**  系统的alert弹出框，不同手机UI效果可有差异。



<span id="ff_2">**toast(jsonData:Object): void**</span>  

<code>弹出Toast提示</code>   

参数：  

jsonData：Toast提示传入参数，Json对象，定义如下：  

> content：内容，字符串类型，必选项； 
> 
> duration：持续时间，数字枚举型，可选项，[0,1]
> 
>  - 0：持续时间短（默认）；
> 
> - 1：持续时间长  

返回值：无





<span id="ff_3">**actionSheet(jsonData:Object,callFunction:Function): void**</span>  

<code>弹出底部菜单选择</code>  

参数：  

jsonData：传递菜单参数，Json对象，定义如下：  

> buttonTexts：按钮文字数组，数组类型，必选项；

callFunction：点击触发回调函数，入参为数字，标识点击索引，从0开始，必选参数

返回值：无



<span id="ff_4">**selectDate(jsonData:Object,callFunction:Function): void**</span>  

<code>弹出系统日期选择</code>  

参数：  

jsonDate：日期选择传递参数，Json对象，定义如下： 

>   initDate：初始化日期，字符串类型，格式：YYYY-MM-DD，可选项，若不设置则显示当前日期；

callFunction：点击触发回调函数，必选参数，入参为Json对象定义如下： 

> status：触发状态，数字枚举型，[0,-1]
> 
> -    0：成功选择日期 
> 
> -    -1：取消选择 
> 
> date：已选择日期，字符串类型，格式：YYYY-MM-DD

返回值：无

**注： ** 弹出手机系统日期选择，不同手机效果不一样。


<span id="ff_5">**selectTime(jsonData:Object,callFunction:Function): void**</span>  

<code>弹出系统时间选择</code>  

参数：  

jsonDate：时间选择传递参数，Json对象，定义如下：  

>  initTime：初始化时间，字符串类型，格式：HH24:MI，可选项，若不设置则显示当前时间

callFunction：点击触发回调函数，必选参数，入参为Json对象定义如下：  

> status：触发状态，数字枚举型，[0,-1]  
> 
> -    0：成功选择时间
> 
> -    -1：取消选择  
> 
> time：已选择时间，字符串类型，格式：HH24:MI



<span id="ff_6">**showImages(jsonData:Object): void**</span>  

<code>显示图片集</code>  

参数：  

 jsonData：需显示的图片集参数，Json对象，定义如下：
> 
> config：设置图片集加载控件系统参数配置，Json对象，定义如下：
> 
> - bgColor：图片集加载控件背景色，字符串类型，可选项，支持格式#RRGGBB，如color:#ffffff，默认黑色
> 
> -  statusbarBgColor：图片集加载控件顶部状态栏背景色，字符串类型，格式为#xxxxxx,默认采用系统主题设置，可选项
>  
> -  cache：网络图片是否缓存，数字类型[0,1]，可选项，0：图片不缓存；1：图片缓存（默认）
> 
> -  index：传入页码索引，数字类型，默认从0开始计数，[0,num-1]可选项；
> 
> data：需要传递的图片集参数，数组类型，数组成员为Json对象定义如下：
> 
> - src：需要加载图片路径，字符串类型，必选项，支持本地图片（res：前缀），网络图片（http://前缀）
> 
> - title：新闻标题，字符串类型，可选项
> 
> - content：新闻内容，字符串类型，可选项




<span id="ff_7">**selectFile(jsonData:Object,callBackFun:Function): void**</span>  

<code>通过js实现文件选择器调用</code>  

通过js实现文件选择器调用，实现类似File文件选择控件相似的效果，文件选择成功后将选择文件路径回调。

参数：  

jsonData，Json对象，定义如下： 

> defaultPath：设置默认选择文件夹路径，支持res:、file:前缀方式，字符串类型，可选项，若不设置该属性，则Android默认从SD卡根目录，iOS默认从程序安装目录； 
> 
> filter：设置或返回选中文件时显示给用户的文件类型，字符串类型，支持以下格式：doc、docx、xls、xlsx、ppt、pptx、pdf、txt、html、xml、bmp、jpg、jpeg、png、rar、zip需过滤的文件以“|”连接，如jpg|png，说明过滤出后缀名为jpg或png的图片文件。可选项，默认为空串即不过滤；

callBackFun，结果回调函数，函数具有json类型入参，必选项，入参定义如下： 

> code：回应状态码，数字[0,-1]。0：用户选择文件成功；-1：用户取消选择文件；  
> 
> filePath：用户选择文件全路径，字符串类型，若用户取消选择，则该值为null；


<span id="ff_8">**selectVideo(jsonData:Object,callBackFun:Function): void**</span>  

<code>选择设备中单个视频</code>  



参数：  

jsonData：Json对象，定义如下： 

> savePath：选择视频后保存目录路径，如savePath=“res:image/video”，字符串类型，必选项；

callBackFun：结果回调函数，函数具有json类型入参，必选项，入参定义如下： 

> code：回应状态码，数字[0,-1]。0：用户选择视频成功；-1：用户取消选择视频； 
> 
> videoPath：选择视频文件全路径，字符串类型，取消选择返回null  
> 
> thumbnailPath：选择视频文件首帧图片，字符串类型，取消选择返回null





<span id="ff_9">**selectImage(jsonData:Object,callBackFun:Function): void**</span>  

<code>选择设备中单张图片</code>  

选择设备中单张图片，结果通过回调函数返回

参数：  

jsonData：Json对象，定义如下：  

> savePath：选择图片后默认保存目录路径，字符串类型，必选项，支持res:、file:前缀方式
> 
> pwidth：选择图片宽度像素值，数字类型，可选项，若不设置则图片不进行压缩；
> 
> isCrop：图片是否进行裁剪。可选参数，bool型，true：裁剪；false：不裁剪（默认）
> 
> cropWidth：裁剪图片宽度像素值，数字类型，可选项；

callBackFun：结果回调函数，函数具有json类型入参，必选项，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：用户选择图片成功；
> 
> - -1：用户取消选择图片；
> 
> imagePath：选择图片文件全路径，字符串类型，取消选择返回null


<span id="ff_10">**selectImages(jsonData:Object,callBackFun:Function): void**</span>  

<code>选择设备中多张图片</code>  

选择设备中多张图片，结果通过回调函数返回

参数：  

jsonData：Json对象，定义如下：  

> savePath：选择图片后默认保存目录路径，字符串类型，必选项，支持res:、file:前缀方式
> 
> pwidth：选择图片宽度像素值，数字类型，可选项，若不设置则图片不进行压缩；
> 
> nums：选择总图片最大张数限制，数字类型，可选项，默认值为5；

callBackFun: 结果回调函数，必选项，函数具有json类型入参，入参定义如下：  

> code ：回应状态码，数字[0,-1]。0：用户选择图片成功；-1：用户取消选择图片；  
> 
> imagePaths：已选择所有图片全路径，字符串数组类型，若用户取消选择则返回空数组
