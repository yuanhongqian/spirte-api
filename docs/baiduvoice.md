# BaiduVoice 百度语音识别

----------

BaiduVoice（语音转文字）工具类，百度语音SDK参考地址：[http://developer.baidu.com/wiki/index.php?title=docs/cplat/media/voice/sdk](http://developer.baidu.com/wiki/index.php?title=docs/cplat/media/voice/sdk)。

使用时需要在js中引入 ：

```javascript
var baiduvoice = require("BaiduVoice"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  


<span id="ff_0">**record(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动百度语音识别</code>  

参数：  

jsonData，百度语音识别参数设置，Json类型，定义如下：

**apiKey**：百度开发云平台认证 apiKey，可选项，若不设置则使用Edn打包配置的apiKey

**secretKey**：百度开发云平台认证 secretKey，可选项，若不设置则使用Edn打包配置的secretKey

**language**：百度语音支持语言模式，字符串枚举型[cmn-Hans-CN，yue-Hans-CN，sichuan-Hans-CN，en-GB]，可选项。若不设置则默认cmn-Hans-CN中文普通话。cmn-Hans-CN：中文普通话；yue-Hans-CN：中文粤语；en-GB：英文

**prop**：百度语音识别模式，字符串枚举型[input，music，video，app，web，search，shopping，health，phone，song，medical，car，catering，finance，game，recipes，assistant，map]，可选项。默认为input输入模式

**prompt**：语音输入对话框提示语，可选项，若不输入则提示"请说话"，字符串类型，仅Android支持

**description**：语音输入对话框底部默认描述语，可选项。默认为空，仅Android支持

**theme**：弹出框样式选择，字符串枚举型[blue_light，blue_deep,red_light,red_deep,green_light,green_deep,orange_light,orange_deep]，可选项，默认为blue_light亮蓝样式

callBackFun：结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> - 0：成功；
> 
> - -1：语音识别失败
> 
> result：语音识别结果，字符串类型

**注：** 百度语音识别需要保证设备联网



