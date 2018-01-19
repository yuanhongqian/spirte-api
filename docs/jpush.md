# JPush  极光Push推送类 

----------

JPush 组件,用于实现对接极光Push推送模块相关功能。

使用JPush推送需要先到极光推送官网注册开发者账号，要创建极光推送开发者帐号，请访问极光推送官方网站[https://www.jiguang.cn/push](https://www.jiguang.cn/push)

<image src="image/jpush_1.png"/>

创建帐号成功并登录后，进入极光控制台后，点击“创建应用”按钮。创建帐号进入极光推送后，首先显示的是创建应用的界面。若Android应用，则填上你的应用程序的名称以及Android包名这两项就可以了；若iOS应用，则需要上传Apns证书，并填写应用名。创建成功后会生成应用唯一AppKey。

<image src="image/jpush_2.png"/>


JPush并非Sprite的默认模块，若应用需要使用极光推送，则Edn或MBuilder打包是需要勾选极光推送模块，并填写appKey和channel。

使用JPush组件来实现极光推送相关功能，相关方法调用可放置于任意页面中，但事件监听必须放置于homeJs应用入口JS中。

使用时需要在js中引入 ：

```javascript
var jpush = require("JPush"); 
```

**注：** 该组件为外置功能组件，打包需要选择。。

<h2 id="cid_1">js方法</h2>  

本节目录：


>[ init(): void  初始化并启动极光推送JPush](#ff_0)
> 
>[ getRegistrationId(): string  获取注册成功后JPush服务器分配的设备标识](#ff_1)
> 
> [stop(): void  停止极光推送服务](#ff_2)
> 
> [resume(): void   恢复极光推送服务](#ff_3)
> 
> [isStopped(): boolean  检查极光推送服务是否已经被停止](#ff_4)
> 
> [setDebugMode(isDebug: boolean): void  设置调试模式开启/关闭](#ff_5)
> 
> [setAlias(alias: string, callBackFun: Function): void  设置别名](#ff_6)
> 
> [setTags(tags: Array&lt;string&gt;, callBackFun: Function): void  设置标签](#ff_7)
> 
> [getVersion(): string  获取JPush SDK版本信息](#ff_9)
> 
> **android**
> 
>[ setLatestNotificationNumber(maxNumber: number): void  限制状态栏保留的通知条数](#ff_10)
> 
> [clearAllNotifications(): void  清除所有通知栏信息](#ff_11)
> 
> [clearNotificationById(messageId: string): void  清除指定通知栏信息](#ff_12)
> 
> [setPushTime(info: object): void  设置推送时间](#ff_13)
> 
> [setSilenceTime(info: object): void  设置推送通知静默时间](#ff_14)
> 
> **ios**
> 
>[ setBadge(badge: number): boolean  设置JPush服务器中存储的badge值](#ff_15)
> 
>[ resetBadge(): void  清空JPush服务器中存储的badge值](#ff_16)
 



<span id="ff_0">**init (): void**</span>  

<code>初始化并启动极光推送JPush</code>  

参数：无 

返回值：无

**注：** 该方法建议在程序入口js中使用

<span id="ff_1">**getRegistrationId(): string **</span>  

<code>获取注册成功后JPush服务器分配的设备标识</code>  

参数：无

返回值：集成了 JPush SDK 的应用程序成功注册到 JPush 服务器时，JPush 服务器会给客户端返回一个唯一的该设备的标识


<span id="ff_2">**stop(): void  **</span>  

<code>停止极光推送服务</code>   

参数：无  

返回值：无  

**注： **

> Android停止极光推送服务
> 
> iOS使推送或 DeviceToken 失效

<span id="ff_3">**resume(): void **</span>  

<code>恢复极光推送服务</code>      

参数：无 

返回值：无 

**注：**

> Android极光推送完全恢复正常工作
> 
> iOS重新去 APNS 注册


<span id="ff_4">**isStopped(): boolean**</span>  

<code>检查极光推送服务是否已经被停止</code>    

参数：无 

返回值：push服务是否被停止，true：push服务被停止；false：push服务正常运行


**注：**
> 
> Android用来检查 Push Service 是否已经被停止。
> 
> iOS平台检查推送服务是否注册。  



<span id="ff_5">**setDebugMode(isDebug: boolean): void  **</span>  

<code>设置调试模式开启/关闭</code>  

参数： 

isDebug：是否开启调试模式，boolean型，true：调试模式开启；false：调试模式关闭；

返回值：无



<span id="ff_6">**setAlias(alias: string, callBackFun: Function): void **</span>  

<code>设置别名</code>   

参数：

> alias：需要设置的别名，字符类型
> 
callBackFun：设置别名结果回调，参数为Json对象，定义如下：

> code：结果码，数字类型，0：设置成功；其他值：设置失败；错误码参见极光官网文档

返回值：无 

**注：** 

> 1：空字符串表示取消之前的设置
> 
> 2：每次调用设置有效的别名，覆盖之前的设置
> 
> 3：有效的别名组成：字母（区分大小写）、数字、下划线、汉字、特殊字符(v2.1.6支持)@!#$&*+=.|
> 
> 4：限制：alias 命名长度限制为 40 字节



<span id="ff_7">**setTags(tags: Array&lt;string&gt;, callBackFun: Function): void**</span>  

<code>设置标签</code>   

参数：

tags：需要设置的标签，字符串数组类型

callBackFun：设置标签结果回调，参数为Json对象，定义如下： 

> code：结果码，数字类型，0：设置成功；其他值：设置失败；错误码参见极光官网文档

返回值：无 

**注：** 

> 1：空数组表示取消之前的设置
> 
> 2：每次调用至少设置一个 tag，覆盖之前的设置，不是新增
> 
> 3：有效的标签组成：字母（区分大小写）、数字、下划线、汉字
> 
> 4：限制：每个 tag 命名长度限制为 40 字节，最多支持设置 100 个 tag，但总长度不得超过1K字节:
> 
> 5：单个设备最多支持设置 100 个 tag


<span id="ff_8">**getVersion(): string**</span>  

<code>获取JPush SDK版本信息</code>

参数：无 

返回值：JPush SDK版本信息,字符串类型


<span id="ff_9">**setLatestNotificationNumber(maxNumber:number):void**</span>  

<code>获取JPush 限制状态栏保留的通知条数</code>

限制状态栏保留的通知条数。默认为保留最近 5 条通知 

参数：

maxNumber：限制状态栏保留的通知条数，数字类型，必选项

返回值：无

注：仅Android支持 


<span id="ff_10">**clearAllNotifications():void**</span>  

<code>清除所有通知栏信息</code>  

参数：无

返回值：无

注：仅Android支持

<span id="ff_11">**clearNotificationById(messageId:id):void**</span>  

<code>清除指定通知栏信息</code>

参数： 

messageId：唯一标识消息的Id，字符串类型

返回值：无 

注：仅Android支持

<span id="ff_12">**setPushTime (info:object): void**</span>  

<code>设置推送时间</code>  

参数：

info：推送时间设置，json格式定义如下：

>   weekDays：数组类型，数组成员为数字，范围为0-6,0表示星期日，6表示星期六
>   
>   startHour：允许推送的开始时间，数字类型，24小时制
>   
>   endHour：允许推送的结束时间，数字类型，24小时制
>   
返回值：无

注：仅Android支持

<span id="ff_13">**setSilenceTime (info:object): void**</span>  

<code>设置推送通知静默时间</code>    

参数：

info：推送静默时间设置，json格式定义如下：

>   startHour：静音时段的开始时间 ，数字类型， 单位小时 （24小时制，范围：0~23 ）  
>   
>   startMinute：静音时段的开始时间 ，数字类型， 单位分钟（范围：0~59）
>   
>   endHour：静音时段的结束时间 ，数字类型， 单位小时 （24小时制，范围：0~23 ）  
>   
>   endMinute：静音时段的结束时间 ，数字类型， 单位分钟（范围：0~59）
>   
返回值：无

注：仅Android支持

<span id="ff_14">**setBadge(badge:number):boolean**</span>  

<code>设置JPush服务器中存储的badge值</code>  

参数： 

badge：JPush服务器中存储的badge值，数字类型，取值范围：[0,99999]

返回值：bool型，true：设置成功，false：设置失败

**注：**

>  badge是iOS用来标记应用程序状态的一个数字，出现在程序图表右上角。 JPush封装badge功能，允许应用上传badge值至JPush服务器，由JPush后台帮助管理每个用户所对应的推送badge值，简化了设置推送badge的操作，若直接设置本地badge则调用Device组件setBadgeNumber方法即可
> 
> 仅iOS支持


<span id="ff_15">**resetBadge():void	**</span>  

<code>清空JPush服务器中存储的badge值</code>  

参数：无

返回值：无

注：仅iOS支持


<h2 id="cid_2">事件</h2>  

本节目录：

[registration  向JPush服务器注册](#sj_0)

[messageReceived	收到了自定义消息 ](#sj_1)

[notificationReceived  	接收通知触发回调](#sj_2)

[notificationClick  点击通知触发回调](#sj_3)  

Android	 

[connectionChange  JPush连接服务状态发送变化触发](#sj_4)




<span id="sj_0">**registration**</span>

<code>向JPush服务器注册</code>

向JPush服务器注册，获取注册Id回调，event事件对象包括：

>     type：事件类型,字符串类型,固定值：registration；
>     
>     target：触发事件的目标组件 
>     
>     timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下：

> registrationId：SDK 向 JPush Server 注册所得到的注册 全局唯一的 Id ，可以通过此 Id向对应的客户端发送消息和通知，字符串类型

**注：** 该事件需要在应用入口homeJs中监听


<span id="sj_1">**messageReceived**</span>

<code>收到了自定义消息</code>

收到了自定义消息 Push回调,event事件对象包括：

>     type：事件类型,字符串类型,固定值：messageReceived；
>     
>     target：触发事件的目标组件 
>     
>     timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下：
> 
> title：保存服务器推送下来的消息的标题,对应 API 消息内容的 title 字段，字符串类型
> 
> message：保存服务器推送下来的消息内容，对应 API 消息内容的 message 字段，字符串类型
> 
> extra：保存服务器推送下来的附加字段，对应 API 消息内容的 extras 字段，json字符串类型
> 
> messageId：唯一标识消息的Id，字符串类型，注：仅Android支持

**注：**

> 1：该事件需要在应用入口homeJs中监听
> 
> 2：自定义消息不会构建通知栏，且仅在程序运行时接收


<span id="sj_2">**notificationReceived**</span>

<code>收到了自定义消息</code>

接收通知触发回调,event事件对象包括：  

> type：事件类型,字符串类型,固定值：notificationReceived；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下：  

> title：保存服务器推送下来的通知的标题,对应 API 消息内容的 title 字段，字符串类型
> 
> message：保存服务器推送下来的通知内容，对应 API 消息内容的 alert 字段，字符串类型
> 
> extra：保存服务器推送下来的附加字段，对应 API 消息内容的 extras 字段，json字符串类型
> 
> messageId：唯一标识消息的Id，字符串类型，注：仅Android支持
> 
> badge：快捷图表显示数字,数字类型,注：仅iOS支持

**注：** 该事件需要在应用入口homeJs中监听  


<span id="sj_3">**notificationClick**</span>

<code>点击通知触发回调</code>

点击通知触发回调,event事件对象包括： 

>     type：事件类型,字符串类型,固定值：notificationClick；
>     
>     target：触发事件的目标组件 
>     
>     timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下：
> 
> title：保存服务器推送下来的通知的标题,对应 API 消息内容的 title 字段，字符串类型，
> 
> message：保存服务器推送下来的通知内容，对应 API 消息内容的 alert 字段，字符串类型
> 
> extra：保存服务器推送下来的附加字段，对应 API 消息内容的 extras 字段，json字符串类型
> 
> messageId：唯一标识消息的Id，字符串类型，注：仅Android支持
> 
> badge：快捷图表显示数字,数字类型,注：仅iOS支持

**注：** 该事件需要在应用入口homeJs中监听


<span id="sj_4">**connectionChange**</span>

<code>JPush连接服务状态发送变化触发</code>
   
JPush连接服务状态发送变化触发,event事件对象包括：  

> type：事件类型,字符串类型,固定值：connectionChange；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
> 

param对象为Json对象,定义如下：  

>  isConnected：JPush连接是否已正常连接，bool型，true：已连接；false：已断连

**注： **
> 
> 该事件需要在应用入口homeJs中监听
> 仅Android支持

