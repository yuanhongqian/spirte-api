# VideoUtil 视频操作类

----------

VideoUtil 视频操作类，支持视频播放，小视频录制等功能。

使用时需要在js中引入 ：

```javascript
var videoutil = require("VideoUtil"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ recordShortVideo(jsonData:Object,callFunction:Function): void  启动小视频录制 ](#ff_0)
> 
> [openVideo(jsonData:Object): void  调用系统播放器播放视频 ](#ff_1)



<span id="ff_0">**recordShortVideo(jsonData:Object,callFunction:Function): void**</span>  

<code>启动小视频录制</code>     

参数：  

jsonData：打开小视频拍摄界面传入参数，Json对象定位如下：  

>    path：录制小视频生成文件全路径路径（mp4格式），支持res: file:，字符串类型，必选项；
>     
>    theme：小视频拍摄界面风格，[dark，light]，默认dark，字符串枚举类型，可选项；
>    
>    minTime：录制最短时间，数字类型，单位秒，可选项，默认3秒，最小2s；
>    
>    maxTime：录制最长时间，数字类型，单位秒，可选项，默认10s，最大60s；

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字[0,-1]
> 
> - 0：录制小视频成功；
> 
> - -1：用户取消录制；
> 
> data：Json对象，code为0时该值存在，code为-1时该值为null，每项定义如下：
> 
> - path：生成小视频文件全路径，字符串类型；
> 
> - thumbnailPath：拍摄完成后生成小视频首帧图片全路径，字符串类型 
> 
> time：录制时长，单位秒，数字类型

返回值：无

**注：** maxTime需大于minTime

示例：

```javascript
 var videoutil = require("VideoUtil");
var path = "res:spriteClient/page/function_component/multimedia/videoutil/res_video.mp4";
var theme = "dark";
var minTime = 2;
var maxTime = 15;

var json = {};
json.path = path;
json.theme = theme;
json.minTime = minTime;
json.maxTime = maxTime;
videoutil.recordShortVideo(json,function(dataJson){
 	var code = dataJson.code;
        var data = dataJson.data;
        var content = "";
        if( code==0 ){
            content = "录制小视频成功\n生成小视频文件全路径:"+data.path+"\n拍摄完成后生成小视频首帧图片全路径:"+data.thumbnailPath   +"\n录制时长:"+data.time+"秒";      
        }else if( code==-1 ){
            content = "用户取消录制\ndata值应为null,实际为"+data;
        }else{
            content = "录制异常:"+code;
        }
});

```


<span id="ff_1">**openVideo(jsonData:Object): void**</span>  

<code>调用系统播放器播放视频</code>   

支持本地及网络视频

参数：  

jsonData：打开系统播发器入参数，Json对象定位如下： 

> videoPath：需要播放视频路径，字符串类型
> 
> - 本地路径：res: file:前缀
> 
> - 网络路径：http:前缀

返回值：无
