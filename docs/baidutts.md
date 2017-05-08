# BaiduTts  百度语音合成（文字转语音）工具类

----------

BaiduTts 百度语音合成（文字转语音）工具类，需要对应用进行授权验证才能够使用，开发人员需要主动至百度TTS平台注册应用相关信息：http://app.navi.baidu.com/ttsregister/appinfo，TTS注册流程：[http://developer.baidu.com/map/index.php?title=android-navsdk/guide/voice](http://developer.baidu.com/map/index.php?title=android-navsdk/guide/voice)。

使用时需要在js中引入 ：

```javascript
var baidutts = require("BaiduTts"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  


<span id="ff_0">**play(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动百度语音TTS播放</code>  

参数：  

jsonData，百度语音播放参数设置，Json类型，定义如下：

> apiKey：百度开发云平台认证apiKey，可选项，若不设置则使用Edn打包配置的apiKey。
> 
> secretKey：百度开发云平台认证secretKey，可选项，若不设置则使用Edn打包配置的secretKey
> 
> content：需要朗读的内容，字符串，必选项
> 
> speaker：声音模式，字符串枚举型，[female,male],默认female，可选项。 
> 
> volume：音量，数字[1~10],默认5。1表示，小音量，10表示最大音量。可选项
> 
> speed：语速，数字[1~10],默认5。1表示最慢语速，10表示最大语速。可选项
> 
> pitch：语调，数字[1~10],默认5。1表示最低语调，10表示最高语调。可选项

callBackFun：结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。0：成功；其他值：失败

**注：** 百度语音合成需要保证设备联网，若未联网则无法朗读