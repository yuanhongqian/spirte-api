# App 应用信息操作类

----------


App应用信息操作类是应用级的，如果在某个页面使用App做事件监听，只要这个页面没有被关闭，就会影响整个应用，所以开发者在使用这个App类的时候，如果只希望当前页面受到事件监听的影响，可以通过window类来isTop()方法判断当前页面窗口是否是置顶窗口。 比如我们监听back返回键时，事件里面做了当前窗口关闭，如果不做判断，那么所有页面只要是监听了返回事件的都会触发，所有页面就全部关闭了。

使用时需要在js中引入 ：

```javascript
var app = require("App"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>

本节目录：

> [exit(content:string): void  退出程序，弹出alert提示](#ff_1)
> 
> [exitNoAsk(): void  直接退出程序 ](#ff_2) 
> 
> [background(): void  切换程序至后台](#ff_3)
> 
> [reload(): void  重启程序](#ff_4)
> 
>  [getVersion(): string  获取应用版本信息](#ff_5)
> 
>  [getSdkVersion():string  获取SDK版本信息 ](#ff_6)



<span id="ff_1">**exit(content:string): void**</span>  

<code>退出程序，弹出alert提示</code>  

参数：  

content：alert提示框内容，字符串，必选项。

返回值：无

**注：**  此函数可快速构建退出程序功能，若需定制退出无提示则采用exitNoAsk函数

示例：

```javascript

var title = document.getElement("title");
title.on("rtextClick", function (e) {
    app.exit("即将退出Sprite演示应用");
});

```

<span id="ff_2">**exitNoAsk(): void**</span>  

<code>直接退出程序</code> 

参数：无

返回值：无

示例：

```javascript
var title = document.getElement("title");
title.on("rtextClick", function (e) {
    app.exitNoAsk();
});
```



<span id="ff_3">**background(): void**</span>  

<code>切换程序至后台</code>    

参数：无

返回值：无

**注：** 仅Android支持



<span id="ff_4">**reload(): void**</span>  

<code>重启程序</code>  

参数：无  

返回值：无 


<span id="ff_5">**getVersion(): string**</span>  

<code>获取应用版本信息</code> 

参数：无

返回值：应用版本信息,字符串类型

注： 这里获取的打包后的应用版本信息，不是入口文件app.json里面定义的版本（应用资源版本）。


<span id="ff_5">**getSdkVersion():string**</span>  

<code>获取SDK版本信息</code> 

参数：无 

返回值：SDK版本信息,字符串类型

 


<h2 id="cid_2">事件</h2> 

事件的操作支持以下方法：

> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Function&gt;  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_4)   

本节目录：

[back  监听点击设备返回键触发 ](#sj_1) 

[menu   监听点击设备菜单键触发](#sj_2)  

[activate  监听程序从后台被切换至前台时执行触发 ](#sj_3)

[inactivate  监听程序从前台被切换至后台时执行触发](#sj_4)

[orientation  监听设备横竖屏切换时触发](#sj_4) 

[launch  应用程序被启动时触发](#sj_5)


<span id="sj_1">**back**</span>  

<code>监听点击设备返回键触发</code>  

event事件对象包括：

> type：事件类型，字符串类型，固定值：back；
> 
> target：触发事件的目标组件，app类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

**注：** 仅Android支持

示例：

```javascript
app.on("back",function(){
	//app监听事件属于应用级，所有页面只要做了监听，都是监听到该返回时间，如果只希望当前页页面做监听触发操作，需要通过window类里面isTop方法判断当前页面是否是置顶页面
});
```

<span id="sj_2">**menu**</span>  

<code>监听点击设备菜单键触发</code>  

event事件对象包括：

> type：事件类型，字符串类型，固定值：menu；
> 
> target：触发事件的目标组件，app类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

**注：** 仅Android支持

示例：

```javascript
var app = require("App");
app.on("menu",function(){

});
```

<span id="sj_3">**activate**</span>  


<code>监听程序从后台被切换至前台时执行触发</code>  

event事件对象包括：

> type：事件类型，字符串类型，固定值：activate；
> 
> target：触发事件的目标组件，app类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型


示例：

```javascript
var app = require("App");
app.on("activate",function(){

});
```

<span id="sj_4">**inactivate**</span>  

<code>监听程序从前台被切换至后台时执行触发</code>  

event事件对象包括：

> type：事件类型，字符串类型，固定值：inactivate；
> 
> target：触发事件的目标组件，app类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型


<span id="sj_5">**orientation**</span>  

<code>监听设备横竖屏切换时触发</code>   

event事件对象包括： 

> type：事件类型，字符串类型，固定值：orientation；
> 
> target：触发事件的目标组件，app类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型 

orientation：接收当前设备方向，标识设备方向，字符串枚举型，[landscape, portrait]

> landscape：横屏；
> 
> portrait：竖屏；

示例：

```javascript
var app = require("App");
app.on("orientation",function(e,orientation){
     if(orientation =="landscape"){
        //横屏状态处理
     }else if(orientation =="portrait"){
        //竖屏状态处理
     }
 });
```


<span id="sj_6">**launch**</span>  

<code>应用程序被启动时触发</code> 

该事件用于在程序入口js中配置使用，event事件对象包括：  

> type：事件类型，字符串类型，固定值：launch；
> 
> target：触发事件的目标组件，app类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param：Json对象，定义如下：  

> type：启动类型，字符串枚举型，[normal,app，notification，localNotification]；
> 
> - normal：正常桌面启动；
> 
> - app：其他应用调用启动；
> 
> - notification：推送消息启动；
> 
> - localNotification：本地通知启动；
> 
> data：启动传递参数，不同场景下定义如下：
> 
> - 正常启动：值为null；
> 
> - 其他应用启动：Android值为Json对象，iOS值为字符串类型
> 
> - 推送消息启动：值为Json对象
> 
> - 本地通知启动：值为Json对象
 
