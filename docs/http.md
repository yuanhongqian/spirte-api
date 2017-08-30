# Http 网络连接类

----------

Http网络连接类，支持GET/POST/PUT/DELETE，支持ajax()，formSubmit()，download()三种场景调用方式。


使用时需要在js中引入 ：

```javascript
var http = require("Http"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ ajax(option:Object,callFunction:Function):string   ajax异步请求 ](#ff_0)
> 
> [formSubmit (option:Object,callFunction:Function,requestProgressFunction:Function,responseProgressFunction:Function):string 异步表单提交 ](#ff_1)
>
>[download(option:Object,callFunction:Function, responseProgressFunction:Function)   异步文件下载 ](#ff_2)
>
>[ cancel(id:string): void   关闭http请求 ](#ff_3)


<span id="ff_0">**ajax(option:Object,callFunction:Function):string**</span>  

<code>ajax异步请求</code>    

从第三方http/https服务器获取数据，请求/回应均为字符串类型的http交互，支持GET/POST/PUT/DELETE四种请求方式。

参数：  

option：需要设置请求参数，Json对象，定义如下：  

> **url**：请求的主体，字符串类型,必选项  
> 
> **method**：请求的 HTTP 方法，字符串枚举类型，可选项，值包括 GET/POST/PUT/DELETE，默认GET方式  
> 
> **data**：需要传递数据，字符串类型，可选项，默认空串。对于GET/DELETE类型请求，实际发送为url+data；对于POST/PUT类型请求，data为需要发送数据
> 
> **requestHeader**：自定义请求头。Json类型，可选项，默认空，注意不支持设置cookie头
> 
> **isBlock**：采用阻塞或非阻塞方式上传，即是否显示进度条，bool型，可选项，true：显示进度条；false：不显示进度条（默认）
> 
> **timeout**：读取超时时间，数字，单位秒，可选项，默认45s，若读取超时则进入失败回调函数中（状态码404）
> 
> **connectTimeout**：连接超时时间，数字，单位秒，可选项，默认15s，若连接超时则进入失败回调函数中（状态码404），IOS不支持该参数。
> 
> **reqCharset**：请求编码方式，字符串枚举型，可选项，[UTF-8，GBK] , 默认UTF-8
> 
> **rspCharset**：回应体编码方式，字符串枚举型，可选项，优先根据第三方服务器响应的Content-Type中的charset字段确定，若无则根据设置编码[UTF-8，GBK] , 默认UTF-8;
> 
> **isCheckCert**：是否对服务端ssl证书进行校验，https连接时生效。bool型，可选项，默认false，true：校验服务端ssl证书；false：不校验服务端ssl证书，ios必须做校验
> 
> **certPath**：证书加载本地路径，isCheckCert为true时生效，支持本地路径，file:、res:前缀，字符串类型，可选项，Android加载证书格式为.bks，iOS加载证书格式为.cer，使用时需要注意区分  
> 
> **certPassword**：证书密码，isCheckCert为true时生效，字符串类型。.bks格式需要设置，可选项
>    
> **message**：用户自定义数据，JSON类型，可选项；


callFunction：响应结果回调函数，入参为Json对象，定义如下：  

> **status**：服务器返回状态码，数字，状态码在200~299之间为成功，其他值失败，-1标示用户主动取消  
> 
> **data**：服务器返回数据，字符串类型  
> 
>  **headers**：服务器回应头，Json对象
> 
> **message**：用户自定义数据，JSON类型，可选项；
 
返回值：http请求标识，字符串类型；


示例：

```javascript
var option = {};
option.url = "http://iyouqu.com.cn:8080/app/newsActivity/service.do";
option.method = "POST";
option.data = "username=lihua&password=123456";
option.reqCharset = "utf-8";
option.isBlock = false;
http.ajax(option, function (json) {
   if(json.status == 200){
	//成功
	console.log(json.data);
   }

});

```


<span id="ff_1">**formSubmit (option:Object,callFunction:Function,requestProgressFunction:Function,responseProgressFunction:Function):string**</span>  

<code>异步表单提交</code>

向第三方http/https服务器上传包含二进制文件的表单数据，支持POST/PUT两种请求方式

参数：  

option：需要设置请求参数，Json对象，必选参数，定义如下：  

> **url**：请求的主体，字符串类型,必选项  
> 
> **method**：请求的 HTTP 方法，字符串枚举类型，可选项，值包括 POST/PUT，默认POST方式  
> 
> **data**：需要传递数据，数组类型（元素为Json对象），数组元素Json对象定义如下：  
> 
> - type：设置提交数字类型，数字，0：普通类型（默认）1：文件类型
> 
> - name：设置需提交name值, 字符串类型
> 
> - value：设置需提交value值，字符串类型，若type为普通类型，该值为需要提交的value值；若type为文件类型，该值为需要提交的文件路径（res: file:前缀）  
> 
> **requestHeader**：自定义请求头。Json类型，可选项，默认空，注意不支持设置cookie头
> 
> **isBlock**：采用阻塞或非阻塞方式上传，即是否显示进度条，bool型，可选项，true：显示进度条（默认）；false：不显示进度条
> 
> **timeout**：读取超时时间，数字，单位秒，可选项，默认45s，若读取超时则进入失败回调函数中（状态码404）
> 
> **connectTimeout**：连接超时时间，数字，单位秒，可选项，默认15s，若连接超时则进入失败回调函数中（状态码404），IOS不支持该参数。
> 
> **reqCharset**：请求编码方式，字符串枚举型，可选项，[UTF-8，GBK] , 默认UTF-8
> 
> **rspCharset**：回应体编码方式，字符串枚举型，可选项，优先根据第三方服务器响应的Content-Type中的charset字段确定，若无则根据设置编码[UTF-8，GBK] , 默认UTF-8;
> 
> **isCheckCert**：是否对服务端ssl证书进行校验，https连接时生效。bool型，可选项，默认false，true：校验服务端ssl证书；false：不校验服务端ssl证书，ios必须做校验
> 
> **certPath**：证书加载本地路径，isCheckCert为true时生效，支持本地路径，file:、res:前缀，字符串类型，可选项，Android加载证书格式为.bks，iOS加载证书格式为.cer，使用时需要注意区分
> 
> **certPassword**：证书密码，isCheckCert为true时生效，字符串类型。.bks格式需要设置，可选项
> 
> **message**：用户自定义数据，JSON类型，可选项；

callFunction：响应结果回调函数，必选参数，入参为Json对象，定义如下：  

> **status**：服务器返回状态码，数字，状态码在200~299之间为成功，其他值失败，-1标示用户主动取消  
> 
> **data**：服务器返回数据，字符串类型  
> 
> **headers**：服务器回应头，Json对象  
> 
> **message**：用户自定义数据，JSON类型，可选项；
 

requestProgressFunction：请求进度回调函数，可选参数，入参为Json对象，定义如下：  

> **sendLength**：已提交文件字节数，数字
> 
> **totalLength**：文件总字节数，数字
> 
> **message**：用户自定义数据，JSON类型，可选项；
 

responseProgressFunction：响应进度回调函数，可选参数，入参为Json对象，定义如下：  

> **receivedLength**：已接收文件字节数，数字
> 
> **totalLength**：文件总字节数，数字
> 
> **message**：用户自定义数据，JSON类型，可选项；

返回值：http请求标识，字符串类型；

示例：

```javascript

var option = {};
var submitBase = "http://192.168.7.1:8180/ademo/up";

//普通参数
var data_key = {};
data_key.type = 0;
data_key.name = "key";
data_key.value = "a06bebae5f472c4a2342c165e7a6b3e7";

//带附件参数
var data_resfile = {};
data_resfile.type = 1;
data_resfile.name = "resfile";
data_resfile.value = "res:spriteClient/image/grid/1.jpg";

var data = new Array();
data.push(data_key);
data.push(data_resfile);

option.url = submitBase;
option.data = data;
option.isBlock = false;
option.timeout = 10;
option.method = "POST";

httpId = http.formSubmit(option, function(responseData){
	if(responseData.status >= 200 && responseData.status <= 299){
                text = "网络请求成功";
            }else if(responseData.status == -1){
                text = "用户主动取消网络请求";
            }else{
                text = "网络请求失败，返回HTTP状态码为:" + responseData.status;
            }
});

``` 



<span id="ff_2">**download(option:Object,callFunction:Function, responseProgressFunction:Function)**</span>  

<code>异步文件下载</code>  

从第三方http/https服务器下载二进制文件，请求/回应均为字符串类型的http交互，支持GET/POST/PUT/DELETE四种请求方式 

参数：  

option：需要设置请求参数，Json对象，必选参数，定义如下：  

> **url**：请求的主体，字符串类型,必选项  
> 
> **method**：请求的 HTTP 方法，字符串枚举类型，可选项，值包括 GET/POST/PUT/DELETE，默认GET方式  
> 
> **data**：需要传递数据，字符串类型，可选项，默认空串。对于GET/DELETE类型请求，实际发送为url+data；对于POST/PUT类型请求，data为需要发送数据  
> 
> **path**：下载文件保存到本地目录，字符串类型，res：前缀方式，必选项
>
> **fileName**： 下载文件指定的文件名包括后缀，字符串类型。
> 
> **requestHeader**：自定义请求头。Json类型，可选项，默认空，注意不支持设置cookie头
> 
> **isBlock**：采用阻塞或非阻塞方式下载，即是否显示进度条，bool型，可选项，true：显示进度条（默认）；false：不显示进度条
> 
> **timeout**：读取超时时间，数字，单位秒，可选项，默认45s，若读取超时则进入失败回调函数中（状态码404）
> 
> **connectTimeout**：连接超时时间，数字，单位秒，可选项，默认15s，若连接超时则进入失败回调函数中（状态码404），IOS不支持该参数。
> 
> **reqCharset**：请求编码方式，字符串枚举型，可选项，[UTF-8，GBK] , 默认UTF-8
> 
> **rspCharset**：回应体编码方式，字符串枚举型，可选项，优先根据第三方服务器响应的Content-Type中的charset字段确定，若无则根据设置编码[UTF-8，GBK] , 默认UTF-8;
> 
> **isCheckCert**：是否对服务端ssl证书进行校验，https连接时生效。bool型，可选项，默认false，true：校验服务端ssl证书；false：不校验服务端ssl证书
> 
> **certPath**：证书加载本地路径，isCheckCert为true时生效，支持本地路径，file:、res:前缀，字符串类型，可选项，Android加载证书格式为.bks，iOS加载证书格式为.cer，使用时需要注意区分
> 
> **certPassword**：证书密码，isCheckCert为true时生效，字符串类型。.bks格式需要设置，可选项  
> 
> **message**：用户自定义数据，JSON类型，可选项；

callFunction：响应结果回调函数，必选参数，入参为Json对象，定义如下：  

> **status**：服务器返回状态码，数字，状态码在200~299之间为成功，其他值失败，-1标示用户主动取消  
> 
> **path**：下载成功后文件保存路径，字符串类型  
> 
> **headers**：服务器回应头，Json对象  
> 
> **message**：用户自定义数据，JSON类型，可选项；

responseProgressFunction：下载进度回调函数，可选参数，入参为Json对象，定义如下：  

> **receivedLength**：已下载文件字节数，数字  
> 
> **totalLength**：文件总字节数，数字  
> 
> **message**：用户自定义数据，JSON类型，可选项；

返回值：http请求标识，字符串类型；


示例：

```javascript

var option = {};
var base_https = "https://192.168.7.1:18843/ademo/down";
var data = "file_download_name=app.zip";
var savePath = "res:downloadTemp/file/";

option.url = base_https;
option.data = data;
option.fileName = "app.zip";
option.isBlock = false;
option.timeout = 10;
option.method = "GET";
option.path = savePath;

httpId = httpdownload(option, function(responseData){
	if(responseData.status >= 200 && responseData.status <= 299){
                text = "网络请求成功";
                text += "文件路径:" + responseData.path;
	}
});

``` 

<span id="ff_3">**cancel(id:string): void**</span>  

<code>关闭http请求</code>   

参数：  

id：需要被关闭的http请求标识，字符串类型，必选项  

返回值：无
