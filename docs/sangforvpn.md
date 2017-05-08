# SangforVpn  深信服Vpn工具类

----------

深信服Vpn工具类，用于实现深信服Vpn服务器登录，登出等操作。

使用时需要在js中引入 ：

```javascript
var sangforvpn = require("SangforVpn"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

> [init(jsonData:Object,callBackFun:Function): void    初始化深信服Vpn服务器 ](#ff_0) 
> 
> [login(jsonData:Object,callBackFun:Function): void  登录深信服Vpn服务器 ](#ff_1)
> 
> [logout(callBackFun:Function): void  注销深信服Vpn服务器 ](#ff_2) 
> 
> [smsLogin(jsonData:Object,callBackFun:Function): void  启动深信服vpn短信验证码登录 ](#ff_3) 
> 
> [smsRefresh(): void 向vpn服务器发送通知重新获取短信验证码](#ff_4)
> 
> [getVpnStatus(): number  返回深信服vpn当前连接状态](#ff_5)




<span id="ff_0">**init(jsonData:Object,callBackFun:Function): void**</span>  

<code>初始化深信服Vpn服务器</code>  

参数：  

jsonData，初始化参数设置，Json类型，定义如下：  

> ip：Vpn服务器地址，字符串类型，必选项  
> 
> port：Vpn服务器端口，数字类型，必选项

callBackFun，初始化Vpn服务器结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> - 0：成功；
> 
> - -1：失败

注：若IP和端口发生变化需调用app.reload()方法重载应用


<span id="ff_1">**login(jsonData:Object,callBackFun:Function): void**</span>  

<code>登录深信服Vpn服务器</code>   

参数：  

jsonData，登录参数设置，Json类型，定义如下：

> name：用户名，字符串类型，必选项
> 
> password：密码，字符串类型，必选项
> 
> cerPath：证书文件所在路径，字符串类型，可选项，支持res: file: 前缀
> 
> cerPassword：证书密码，字符串类型，可选项

callBackFun，初始化Vpn服务器结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。
> 
> - 0：登录成功
> 
> - 1：vpn服务器认证失败，该错误一般由于认证用户名、密码错误或证书、密码错误导致
> 
> - 2：请输入收到的短信验证码，进行短信验证
> 
> - 3：vpn服务器设置硬件特征码校验，等待管理员审批 

<span id="ff_2">**logout(callBackFun:Function): void**</span>  

<code>注销深信服Vpn服务器</code>  

参数：  

callBackFun，注销Vpn服务器结果回调函数，函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字 
> 
> - 0：注销成功
> 
> - 1：注销失败

<span id="ff_3">**smsLogin(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动深信服vpn短信验证码登录</code>  

参数:  

jsonData，短信登录参数设置，Json类型，定义如下：  

smsCode：短信验证码，字符串类型，必选项

callBackFun，短信验证码登录结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> - 0：短信登录成功
> 
> - 1：短信登录失败

<span id="ff_4">**smsRefresh(): void**</span>  

<code>向vpn服务器发送通知重新获取短信验证码</code>  

参数：无 

返回值：无

**注：** vpn服务器设置有短信发送间隔周期，如在此间隔周期内多次获取短信验证码则无效

<span id="ff_5">**getVpnStatus(): number**</span>  

<code>返回深信服vpn当前连接状态</code>   

参数：无 

返回值：数字，定义如下：  

> 0：vpn服务器登录成功；
> 
> 1：vpn服务器还未初始化；
> 
> 2：vpn服务器初始化成功，但还未登录；



<h2 id="cid_2">事件</h2>  

<span id="sj_0">**relogin**</span>  

<code>Vpn底层重连事件的回调</code>  

event事件对象包括：

> type：事件类型，字符串类型，固定值：relogin；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param对象为Json对象，定义如下：

> code：回应状态码，数字
> 
> - 1：开始重连
> 
> - 2：重连成功
> 
> - 3：重连失败

