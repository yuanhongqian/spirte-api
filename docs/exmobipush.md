# ExMobiPush 工具类

----------

ExMobiPush工具类，用于实现对接ExMobi或Mplus Push推送模块相关功能。

推送使用说明，参见：Sprite常用功能里面的 [Push推送章节](https://gitdocument.exmobi.cn/sprite-advanced/pushts.html)

该工具类在使用的过程中，事件相关的建议放在程序入口的js文件里面进行监听，方法无所谓可以在页面的任何位置。

使用时需要在js中引入 ：

```javascript
var exmobipush = require("ExMobiPush"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

[init(jsonData:Object): void   初始化Push推送配置 ](#ff_0) 

[start(): void  启动推送服务 ](#ff_1)

[stop(): void  停止推送服务 ](#ff_2) 

[getVersion(): string  获取Push SDK版本信息 ](#ff_3) 

[setWorkday(workday:string): boolean 设置推送工作日](#ff_4)

[getWorkDay(): string  获取配置的推送工作日](#ff_5)

[setDisturbMode(jsonData:Object): boolean  配置工作日推送工作时间](#ff_6)

[getDisturbMode(): Object   获取配置的工作日推送时间](#ff_7)




<span id="ff_0">**init(jsonData:Object): void**</span>  

<code>初始化Push推送配置</code>  

初始化Push推送配置，调用后会停止当前的推送接收，调用开启后继续推送接收

参数：  

jsonData，初始化参数设置，Json类型，定义如下：  

> registerUrl：推送服务器注册地址，格式：http://ip:port/pns，字符串类型，参看exmobi服务端DNS配置获取，必选项 
> 
> pushUrl：推送服务器推送连接地址，格式：ip:port ，字符串类型，参看exmobi服务端DNS配置获取，可选项，仅Android支持
> 
> defaultStartPush：是否开启推送，bool型，仅Android支持 
> 
> - true：开启推送（默认）； 
> 
> - false：不开启推送，可选项，

返回值：无  

**注：**

 - 该方法建议在程序入口js中使用

- 该方法会向ExMobi的PNS服务器注册一些信息，其中包括应用包名和设备的ESN等信息。其中应用包名开发者必须在PNS服务器上进行鉴权后pns才会进行推送。

- sprite标准客户端Android的包名为：com.fiberhome.sprite.client，Ios用的是bundleid：cn.com.fiberhome.sprite


<span id="ff_1">**start(): void**</span>  

<code>启动推送服务</code>   

启动推送服务，结果进入bind事件中

参数：无

返回值：无

**注：** 该方法建议在程序入口js中使用

<span id="ff_2">**stop(): void**</span>  

<code>停止推送服务</code>  

停止推送服务，结果进入unbind事件中

参数：无 

返回值：无





<span id="ff_3">**getVersion(): string**</span>  

<code>获取Push SDK版本信息</code>  

参数：无 

返回值：Push SDK版本信息，字符串类型


<span id="ff_4">**setWorkday(workday:string): boolean**</span>  

<code>设置推送工作日</code>  

参数：  

> workday：工作日参数配置，字符串类型，必须七位，每一位代表一天，顺序为从周一到周日。1代表需要推送，0 带代表不需要推送，例如："1111100" 代表周一到周五需要推送，周六、周日不需要推送

返回值：bool型，true：设置成功；false：设置失败

**注：** 

- 仅Android支持

- 如果IOS也想有类似的效果，建议这种推送策略在服务端执行，由业务系统来控制具体什么时候推送消息。


<span id="ff_5">**getWorkDay(): string**</span>  

<code>获取配置的推送工作日</code>   

参数：无  

返回值：推送工作日设置，字符串类型  

注：仅Android支持


<span id="ff_6">**setDisturbMode(jsonData:Object): boolean**</span>  

<code>配置工作日推送工作时间</code>

配置工作日推送工作时间。开始时间必须小于结束时间，24 小时制

参数：  

jsonData：配置工作日推送时间参数，Json对象，定义如下：

> startHour：开始小时，24 小时制，取值范围 0~23
> 
> endHour：开始小时，24 小时制，取值范围 0~23
> 
> startMinute：开始分钟，取值范围 0~59
> 
> endMinute：结束分钟，取值范围 0~59

返回值：bool型，true：设置成功；false：设置失败

**注：** 仅Android支持


<span id="ff_6">**getDisturbMode(): Object**</span>  

<code>获取配置的工作日推送时间</code>

参数：无  

返回值：配置的工作日推送时间，Json对象，定义如下：  

> startHour：开始小时，24 小时制，取值范围 0~23
> 
> endHour：开始小时，24 小时制，取值范围 0~23
> 
> startMinute：开始分钟，取值范围 0~59
> 
> endMinute：结束分钟，取值范围 0~59
> 
**注：** 仅Android支持


<h2 id="cid_2">事件</h2>  

本节目录：

[bind  启动推送服务回调](#sj_0)

[unbind  关闭推送服务回调](#sj_1)

[message  接收消息触发回调](#sj_2)

[messageClick  点击通知消息触发回调](#sj_3)


<span id="sj_0">**bind**</span>  

<code>启动推送服务回调</code>  

event事件对象包括：  

> type：事件类型，字符串类型，固定值：bind；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param对象为Json对象，定义如下：  

> code：回应状态码，数字类型
> 
> - 0：成功
> 
> - 1：失败  
> 
> message：错误描述，字符串类型  

**注：** 该事件需要在应用入口homeJs中监听

<span id="sj_1">**unbind**</span>  

<code>关闭推送服务回调</code>

event事件对象包括：

> type：事件类型，字符串类型，固定值：unbind；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param对象为Json对象，定义如下：

> code：回应状态码，数字类型
> 
> -  0：成功
> 
> -  1：失败
> 
> message：错误描述，字符串类型

**注：** 该事件需要在应用入口homeJs中监听

<span id="sj_2">**message**</span>  

<code>接收消息触发回调</code>

如果在该事件里面处理页面逻辑，可以实现接受消息后自动打开应用页面的效果，一般情况下建议让用户手动点击消息触发。。

event事件对象包括：

> type：事件类型，字符串类型，固定值：message；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param对象为Json对象，定义如下：

> type：推送类型，字符串类型
> 
> content：推送内容，Json对象，定义如下：
> 
> - titlehead：标题，字符串类型
> 
> - title：内容，字符串类型
> 
> - app：推送消息归属的应用标识，字符串类型
> 
> - subappid：第三方 Native 应用 appid，即应用唯一标识，字符串类型
> 
> - page：用户点击后打开的本地页面地址，字符串类型
> 
> - badge：快捷图标显示数字，数字类型，注：仅ios支持
> 
> - param：自定义透传参数列表，Json对象
> 
**注：** 该事件需要在应用入口homeJs中监听


<span id="sj_3">**messageClick**</span>  

<code>点击通知消息触发回调</code>

event事件对象包括： 

> type：事件类型，字符串类型，固定值：messageClick；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param对象为Json对象，定义如下：

> type：推送类型，字符串类型
> 
> content：推送内容，Json对象，定义如下：
> 
> - titlehead：标题，字符串类型
> 
> - title：内容，字符串类型
> 
> - app：推送消息归属的应用标识，字符串类型
> 
> - subappid第三方 Native 应用 appid，即应用唯一标识，字符串类型
> 
> - page：用户点击后打开的本地页面地址，字符串类型
> 
> - badge：快捷图标显示数字，数字类型，注：仅ios支持
> 
> - param：自定义透传参数列表，Json对象
> 
**注：** 该事件需要在应用入口homeJs中监听
