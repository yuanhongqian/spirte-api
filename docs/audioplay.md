# AudioPlay 音频播放操作类

----------

AudioPlay音频播放操作类 可以用来播放本地应用和网络音乐，音乐格式依赖手机系统能够解析的音乐给格式。


使用时需要在js中引入 ：

```javascript
var audioplay = require("AudioPlay"); 
```

**注：** 该组件为外置功能组件，需打包选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ init(jsonData:Object): void  初始化当前播放音频信息 ](#ff_0)
> 
> [start(): void  播放音频 ](#ff_1)
> 
>[ pause(): void  暂停播放音频](#ff_2)
> 
>[ stop(): void  停止播放音频](#ff_3)
>
>[seekTo(position:number): void  定位到音频的某一点并播放](#ff_4)
>
>[getStatus(): number  当前音频播放状态](#ff_5)
>
>[getDuration(): number  读取音频的总长度](#ff_6)
>
>[getCurrentPosition(): number  读取音频目前播放位置](#ff_7)
>
>[beep(audioPath:string): void  播放本地音频文件](#ff_8)






<span id="ff_0">**init(jsonData:Object): void**</span>  

<code>初始化当前播放音频信息</code>  

参数：  

jsonData：当前播放音频信息，Json对象

>    url：待播放的音频地址，支持本地及网络地址；
>    
>    mediaInfo：iOS系统锁屏播放器界面相关设置，Json对象，可选项，定义如下：  
> 
> -  title: 歌曲名，字符串类型，必选项；
> 
> -  artist: 演唱者，字符串类型，可选项；
> 
> -  albumTitle：专辑名，字符串类型，可选项；
> 
> -   cover：显示于锁屏界面的封面图，可选项，建议图片尺寸640*640

**注：** 播放之前必须先初始化


<span id="ff_1">**start(): void**</span>  

<code>播放音频</code>
 
参数：无

返回值：无

**注：** 调用该方法时，若音频处于暂停状态，则继续播放，若处于未启动状态，则重新播放




<span id="ff_2">**pause(): void**</span>  

<code>暂停播放音频</code>   

参数：无 

返回值：无


<span id="ff_3">**stop(): void**</span>  

<code>停止播放音频</code>  

参数：无  

返回值：无


<span id="ff_4">**seekTo(position:number): void**</span>  

<code>定位到音频的某一点并播放</code> 

参数:  

position：毫秒数，取值范围大于0小于音频文件播放时间

返回值：无

<span id="ff_5">**getStatus(): number**</span>  

<code>当前音频播放状态</code> 

参数：无  

返回值：数字枚举型，[0,1,2] 

> 0：未播放状态；
> 
> 1：播放状态；
> 
> 2：暂停状态；


<span id="ff_6">**getDuration(): number**</span>  

<code>读取音频的总长度</code>  

参数：无 

返回值：音频的长度，数字类型，单位毫秒


<span id="ff_7">**getCurrentPosition(): number**</span>  

<code>读取音频目前播放位置</code>  

参数：无  

返回值：音频的长度，数字类型，单位毫秒  

**注：** iOS仅支持秒级精度


<span id="ff_8">**beep(audioPath:string): void**</span>  

<code>播放本地音频文件</code>   

参数：  

audioPath：本地音频文件路径，res: file: 前缀，字符串类型  

返回值：无






<h2 id="cid_5">事件</h2>  

本节目录： 

> [finish   音频播放完毕后触发](#sj_0)
> 
> [error  音频播放发生错误时触发 ](#sj_1)
> 
> [interrupt  音频播放发生系统中断（如：其他音乐播放）时触发](#sj_2)
> 
> [restore  音频播放系统中断恢复（如：系统来电）时触发](#sj_3)



事件的操作支持以下方法：

> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Function&gt;  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_4)   



<span id="sj_0">**finish**</span>  

<code>音频播放完毕后触发</code>   

event事件对象包括：  

> type：事件类型，字符串类型，固定值：finish； 
> 
> target：触发事件的目标组件，AudioPlay类； 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型  


<span id="sj_1">**error**</span>  

<code>音频播放发生错误时触发</code>    

> type：事件类型，字符串类型，固定值：error； 
> 
> target：触发事件的目标组件，AudioPlay类； 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型  


<span id="sj_2">**interrupt**</span>  

<code>音频播放发生系统中断（如：其他音乐播放）时触发</code>    

> type：事件类型，字符串类型，固定值：interrupt； 
> 
> target：触发事件的目标组件，AudioPlay类； 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型  



<span id="sj_3">**restore**</span>  

<code>音频播放系统中断恢复（如：系统来电）时触发</code>    

> type：事件类型，字符串类型，固定值：restore； 
> 
> target：触发事件的目标组件，AudioPlay类； 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型  


示例：

效果参考：[Sprite官方UI组件 audioplay组件 ](https://gitdocument.exmobi.cn/sprite-official-ui/audioplay.html) 

组件源码参考：  [https://github.com/yuanhongqian/SpriteUI/blob/master/src/sprite_component/audioplay/audioplay.component](https://github.com/yuanhongqian/SpriteUI/blob/master/src/sprite_component/audioplay/audioplay.component)