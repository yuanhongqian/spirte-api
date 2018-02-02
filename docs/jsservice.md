# Js后台执行环境

---------
<h2 id="cid_0">背景</h2>
------
JsService独立于页面存在，可与页面Js实例在JS runtime中并行运行，支持同时运行多个后台JsService示例，JsService实例的生命周期包括创建、刷新、销毁。JsService可实现后台定位，后台上传，后台下载等相关功能。


<h2 id="cid_1">使用范围</h2>
------

<image src="image/jsservice_1.png"/>



<h2 id="cid_2">注意事项</h2>
--------
JsService环境独立于页面，不包含UI元素，因此请不要调用任何包含UI或者UI操作的组件函数，否则会产生不可预知的后果。

Android：采用进程独立的service后台服务来承载JsService，因此程序退出后，后台服务仍然可以正常运行。

iOS：采用独立于页面Js操作类来承载JsService，由于iOS系统限制，若程序被杀掉后，后台Js环境也将被关闭。若程序切换至后台，则Sprite需要配置后台权限(location/music/voip)，JsService方可正常运行，否则将会被系统主动关闭。需要注意的是不当的后台权限配置可能会导致Appstore无法上架。


<h2 id="cid_3">数据交互</h2>
-------
JsService与普通页面之间可通过以下方法实现数据交互，包括：

1：内存数据，如：MemCache应用级存储（程序关闭后不可用），Clipboard系统剪切板等；

2：文件数据，如：DiskCache文件缓存，File标准文件存储等。

3：数据库，如：Db数据库存储，DbCipher加密数据库存储等；

4：通过对App应用级作用域绑定和操作事件来实现，通过App.on(),App.fire();


<h2 id="cid_4">方法</h2>
--------
JsService 后台JS环境操作类，外置组件。

本节目录：

> [start(jsonData:Object):Object 启动JS后台运行](#ff_1)
> 
> [inStarted(jsonData:Object 指定后台Js是否正在运行):boolean](#ff_2)
> 
> [stop(jsonData:Object):boolean 关闭指定后台Js环境](#ff_3)




<span id="ff_1">**start(jsonData:Object):Object**</span>

<code>启动JS后台运行</code>

参数：jsonData：传递参数，json类型，必选项，定义如下：

> path：需要打开本地Js文件地址，支持res:、file:前缀，字符串类型，必选项；
> 
> data：传递附加参数，json类型，后台JS created函数中接收，可选项；

返回值：返回参数，json类型，定义如下：

> id：待执行的后台Js唯一标识，字符串类型



<span id="ff_2">**isStarted(jsonData:Object):boolean**</span>

<code>指定后台Js是否正在运行</code>

参数：

jsonData：传递参数，json类型，必选项，定义如下：

> id：查询Js环境标识，字符串类型，必选项；

返回值：查询Js环境是否正在运行，true：正在运行，false：未运行


<span id="ff_3">**stop(jsonData:Object):boolean **</span>

<code>关闭指定后台Js环境</code>

参数：

jsonData：传递参数，json类型，必选项，定义如下：

> id：需关闭后台Js环境标识，字符串类型，必选项；

返回值：关闭是否成功，true：关闭成功；false：关闭失败

**注：JsService可运行于普通页面Js环境及后台Js环境中**


<h2 id="cid_5">后台Js环境</h2>
-------------
待运行的后台Js需写入后缀为.js的文件中，通过定义的module.exports对象来标识，固定包含created初始化函数，destroy销毁函数。

**初始化**

created函数为后台Js初始化函数，Js引擎加载后即调用，开发人员在该函数中编写需要执行的后台Js代码。

created(id,data)函数支持入参传递，包含2个入参：

> id：Js执行环境标识，字符串类型；
> 
> data：启动传递参数，json类型；


**销毁**

destroy函数为后台Js销毁函数，Js引擎卸载钱调用，开发人员在该函数中编写需要销毁或释放的后台Js代码。


**JS外部导入**

同页面环境Js外部导入一致，采用CommonJS规范，JS模块中通过module.exports实现函数声明，通过require("模块标识")来加载外部JS模块，详见[JS外部导入](https://gitdocument.exmobi.cn/sprite-api/definejs.html)章节

**示例**

文件名myService.js

```javascript
//初始函数定义

function start(id,data){
	//...
}

//销毁函数定义

function stop(){
	//...
}

//初始函数声明
module.exports.created = start;

//销毁函数声明
module.exports.destroy = stop;
```