# AudioRecord 录音操作类

----------

AudioRecord 录音操作类 ，生成格式mp4


使用时需要在js中引入 ：

```javascript
va raudiorecord = require("AudioRecord"); 
```

**注：** 该组件为外置功能组件，需打包选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ start(jsonData:Object): void   开始录音 ](#ff_0)
> 
> [stop(): void  停止录音 ](#ff_1)
> 
>[ getStatus(): number  当前录音状态](#ff_2)
> 
>[ getVolumeRate(): number  获取实时录音音量比例](#ff_3)







<span id="ff_0">** start(jsonData:Object): void **</span>  

<code>开始录音</code>  

参数：  

jsonData：录音设置信息，Json对象  

>    path：录音生成文件路径（包含文件名），支持res: file:，字符串类型，音频文件格式mp4，必选项； 
>    
>    maxTime：最大录音时间，数字类型，单位：秒，可选项，默认60





<span id="ff_1">**stop(): void**</span>  

<code>停止录音</code>  

参数：无  

返回值：无

**注：**  停止录音后不能继续，再次开始后重新开始。






<span id="ff_2">**getStatus(): number**</span>  

<code>当前录音状态</code> 

参数：无 

返回值：数字枚举型，[0,1]

> 0：未录音；
> 
> 1：正在录音；







<span id="ff_3">**getVolumeRate(): number**</span>  

<code>获取实时录音音量比例</code> 

参数：无   

返回值：当前音量，[0-1]，0为最小，1位最大，增减比例0.1  

**注：** 使用定时器与该函数组合，可实现类似微信录音实时音量效果






<h2 id="cid_5">事件</h2>  

本节目录： 

> [finish   录音完毕后触发](#sj_0)
> 
> [error  录音过程中发生错误时触发 ](#sj_1)




事件的操作支持以下方法：

> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Function&gt;  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_4)   



<span id="sj_0">**finish**</span>  

<code>录音完毕后触发</code>   

event事件对象包括：  

> type：事件类型，字符串类型，固定值：finish； 
> 
> target：触发事件的目标组件，AudioRecord； 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型  


<span id="sj_1">**error**</span>  

<code>录音过程中发生错误时触发</code>    

> type：事件类型，字符串类型，固定值：error； 
> 
> target：触发事件的目标组件，AudioRecord； 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型  

示例：

效果参考：[Sprite官方UI组件 audiorecord组件 ](https://gitdocument.exmobi.cn/sprite-official-ui/audiorecord.html) 

组件源码参考：  [https://github.com/yuanhongqian/SpriteUI/blob/master/src/sprite_component/audiorecord/audiorecord.component](https://github.com/yuanhongqian/SpriteUI/blob/master/src/sprite_component/audiorecord/audiorecord.component)