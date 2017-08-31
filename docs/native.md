# Native 原生程序相关操作类

----------

Native原生程序相关操作类，主要用于控制第三方应用启动安装，附件打开，浏览器调用等功能。


使用时需要在js中引入 ：

```javascript
var native = require("Native"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：


> 
>[ openApp(jsonData:Object,callFunction:Function): void   启动第三方应用并传值 ](#ff_0)
> 
> [ openFile(path:string): void  调用系统第三方程序打开指定文件 ](#ff_1)
>
>[ browser(url:string): void   调用系统浏览器打开指定url地址  ](#ff_2)
>
> [apkInstalled(package:string): boolean  设备是否安装apk应用 ](#ff_3)
> 
> [installApk(apkPath:string,callFunction:Function): void   安装指定路径apk安装包  ](#ff_4)
> 
>[ uninstallApk(packageName:string,callFunction:Function): void   卸载指定应用  ](#ff_5)  
>
> [shareText(jsonData:Object): void  调用系统分享文本](#ff_6)
>
> [shareImage(jsonData:Object): void   调用系统分享图片](#ff_7)
> 
> [openSystemSetting(jsonData:Object): void   打开系统设置相关界面，如：蓝牙设置、定位设置、WiFi设置等](#ff_8)


<span id="ff_0">**openApp(jsonData:Object,callFunction:Function): void**</span>  

<code>启动第三方应用并传值</code>  

参数：  

jsonData：启动应用传递参数，Json对象，定义如下：  

> appId：启动第三方应用关键参数，字符串类型，必选项，Android为需启动第三方应用包名，iOS为第三方应用供外部调用的url scheme；  
> 
> activity：启动第三方应用主activity名称，字符串类型，可选项,仅Android使用；  
> 
> params：启动第三方应用传递参数，Json对象，可选项,仅Android使用；
 
callFunction：启动回调函数，，入参为Json对象，定义如下：  
 
> code：回应状态码，数字[0,-1]  
> -  0：启动第三方应用成功； 
> - -1：启动第三方应用失败

返回值：无

示例：

```javascript

function testopenApp() {
    var os = device.getOs();
    var user = encryption.base64Encode("admin@烽火星空");
    var json = {};
    if(os == "Android"){
        // json.appId = "com.fiberhome.gaea.client";
        json.appId ="com.fiberhome.exmobi.client.gaeaclientandroid126894";
        json.activity = "com.fiberhome.gaea.client.html.activity.WelcomActivity";
       
        var params = {};
        params.user = user;
        params.password = "1234qwer!@#$";
        params.token = "eyJhb-GciOiJ-IUzI1NiIs.InR5cCI6IkpXVCJ9";
        json.params = params;
    }else if(os == "iOS"){
        json.appId = "IxckBhrXpePAoUjkQOXb://normal/?user=" + user + "&password=1234qwer!@#$&token=eyJhb-GciOiJ-IUzI1NiIs.InR5cCI6IkpXVCJ9";
    }
    native.openApp(json, openAppCallback);
}

 /*
      @description 启动第三方应用回调函数
 */
function openAppCallback(data) {
    var source = document.getElement("callbackResult");
    if (data.code == 0) {
        source.setText("返回码：" + data.code + "，启动第三方应用成功");
    } else if (data.code == -1) {
        source.setText("返回码：" + data.code + "，启动第三方应用失败");
    }else{
        source.setText("返回码异常为：" + data.code);
    }  
}

```


<span id="ff_1">**openFile(path:string): void**</span>  

<code>调用系统第三方程序打开指定文件</code>

打开文件的软件选择列表属于系统行为，不同手机形式上可能不一样。

参数：  

path：需要打开本地文件地址，支持res: file:前缀，字符串类型，必选项；  

返回值：无





<span id="ff_2">**browser(url:string): void**</span>  

<code>调用系统浏览器打开指定url地址</code>   

执行该方法，会启动弹出系统浏览器来打开url地址页面。

参数：  

url：需要打开url地址，字符串类型，必选项；  

返回值：无





<span id="ff_3">**apkInstalled(package:string): boolean**</span>  

<code>设备是否安装apk应用</code>  

参数：  

package：需查询apk应用包名，字符串类型，必选项  

返回值：设备上应用是否已安装，bool型，true：已安装；false：未安装  

**注：** 仅Android支持


<span id="ff_4">**installApk(apkPath:string,callFunction:Function): void**</span>  

<code>安装指定路径apk安装包</code> 

参数：   

apkPath：需要安装apk安装包路径，字符串类型，必选项；

callFunction：安装回调函数，入参为Json对象，定义如下：  

> code：回应状态码，数字[0,-1]
> 
> -  0：安装成功；
> 
> - -1：安装失败；  

**注：** 仅Android支持  


<span id="ff_5">**uninstallApk(packageName:string,callFunction:Function): void**</span>  

<code>卸载指定应用</code> 

参数：  

packageName：需要卸载应用包名，字符串类型，必选项；  

callFunction：安装回调函数，入参为Json对象，定义如下：  

> code：回应状态码，数字[0,-1]  
> 
> -  0：卸载成功； 
> 
> - -1：卸载失败；  

**注：** 仅Android支持

<span id="ff_6">**shareText(jsonData:Object): void**</span>  

<code>调用系统分享文本</code>

参数：  

jsonData：分享文本，Json对象,定义如下：  

> text：分享文本内容，字符串类型，必选项；  
> 
> title：分享界面标题，字符串类型，可选项，注：仅Android支持

返回值：无



<span id="ff_7">**shareImage(jsonData:Object): void**</span>  

<code>调用系统分享图片</code>   

参数：  

jsonData：分享图片，Json对象,定义如下：  

> imgPath：需分享图片，只支持本地图片,必选项,本地图片路径,支持res: 及 file: 字符串；  
> 
> title：分享界面标题，字符串类型，可选项，注：仅Android支持

返回值：无

<span id="ff_7">**openSystemSetting(jsonData:Object): void**</span>  

<code>打开系统设置相关界面，如：蓝牙设置、定位设置、WiFi设置等</code>   

参数： 

jsonData：传递参数,Json对象,定义如下： 

> type：打开系统设置相关页面传递参数，字符串枚举型，【settings，wifi，mobile，bluetooth，general，notifications，location，about，vpn，touchid，development，nfc】
> 
> - settings：设置主界面
> 
> - wifi：设置-WIFI
>  
> - mobile：设置-蜂窝移动网络
>  
> - bluetooth：设置-蓝牙
>  
> - general：设置-通用
>  
> - notifications:设置-通知
>  
> - location：设置-隐私-定位服务
>  
> - about：设置-通用-关于本机
>  
> - vpn：设置-通用-VPN
>  
> - touchid：设置-TouchId与密码
> 
> - development：开发人员选项设置，仅Android支持
> 
> - nfc：NFC设置界面，仅Android支持 


返回值：无








