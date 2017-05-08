# AccessAuth 鉴权组件类

----------

AccessAuth鉴权组件类，提供了向ExMobi6服务端实现鉴权及绑定的功能。

该组件通过集成ExMobi6 AccessAuth鉴权sdk来实现。 


使用时需要在js中引入 ：

```javascript
var accessauth = require("AccessAuth"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ init (jsonData:Object): void  初始化ExMobi服务端鉴权SDK ](#ff_0)
> 
> [getToken (jsonData:Object,callBackFun:Function): void  ExMobi服务端SDK获取指定服务token值 ](#ff_1)



<span id="ff_0">**init (jsonData:Object): void**</span>  

<code>初始化ExMobi服务端鉴权SDK</code>     

参数：

jsonData：初始化鉴权SDK参数，Json对象定位如下：

> accessCode：从ExMobi管理平台申请的访问码，字符串类型，必选项；

返回值：无



<span id="ff_1">**getToken (jsonData:Object,callBackFun:Function): void**</span>  

<code>ExMobi服务端SDK获取指定服务token值</code>   

参数： 

jsonData：获取token值传入参数，Json对象定位如下：

> url：服务器地址，支持http和https请求，字符串类型，必选项，格式如：https://miap.cc:8443


callbackFun：用户授权认证回调函数，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字枚举型 [-1,0,其他值] 
> 
> - -1:其他异常
> 
> - 0成功 
> 
> - 8101访问码不存在 
> 
> - 8102应用包不存在 
> 
> - 8103 访问码为禁用状态 
> 
> - 8104参数格式不对
> 
> - 8105 访问码为空，鉴权失败 
> 
> - 8106 访问码已过期 
> 
> - 8107 应用与访问码关系不匹配
> 
> message:响应信息，字符串类型
> 
> token：服务器回应token码，字符串类型，成功时生效,失败则返回null

返回值：无
