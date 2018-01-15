#  LocalNotification 本地通知类

----------
LocalNotification 本地通知类，用于实现系统本地通知功能。

LocalNotification为外置组件，注：仅iOS支持。

使用时需要在js中引入 ：

```javascript
var localnotification = require("LocalNotification"); 
```


<h2 id="cid_1">js方法</h2>  

本节目录：

> [addAlarm(jsondata:Object,callFunction:Function):void 添加本地通知](#ff_0)
> 
> [getAlarm(id:String):Object 获取已设置本地通知信息](#ff_1)
> 
> [getAlarms():Array&lt;Object&gt; 获取已设置所有本地通知提醒新](#ff_2)
> 
> [removeAlarm(id:String):void 删除已设置指定标识本地通知信息](#ff_3)
> 
> [removeAlarms():void 删除所有已设置本地通知提醒设置](#ff_4)


<span id="ff_0">**addAlarm(jsonData:Object,callFunction:Function): void**</span>  

<code>添加本地通知</code>  

参数： 

jsonData：设置本地通知传入参数，Json对象，定义如下：  
> message：通知栏提示内容，字符串类型，必选项
> 
> extra：附加字段，json类型，可选项
> 
> start：首次提醒时间，数字类型，设置的日期和时间距1970年1月1日午夜之间的毫秒数，必选项
> 
> circle：循环周期，字符串枚举型【once，day，week，month，year】，可选项
> 
> - once：仅一次，不重复。默认
> 
> - day：每天重复；
> 
> - week：每周重复，如设置日程提醒为周二 15：30，则后续周周二15：30均进行提醒；
> 
> - month：每月重复，如设置日程提醒日期为8月6日 15:30,则后续月份6日 15：30均进行提醒；
> 
> - year：每年重复，如设置日程提醒日期为8月6日 15：30，则下年8月6日 15：30均进行提醒

callFunction：操作回调函数，函数具有Json类型入参，入参定义如下：

>  code：回应状态码，数字【0，-1】
>  
> - 0：设置本地通知成功
> 
> - -1：设置本地通知失败 
> 
> id：成功设置的通知编号，字符串类型

 
返回值：无


<span id="ff_1">**getAlarm(id:String):Object**</span>

<code>获取已设置本地通知信息</code>

参数：

id：本地通知id，字符串类型，必选项

返回值：已设置本地通知信息，json格式，定义如下：

> id：通知标识，字符串类型
> 
> title：通知标题栏，字符串类型
> 
> message：通知栏提示内容，字符串类型
> 
> extra：附加字段，json类型
> 
> start：开始时间，数字类型
> 
> circle：循环周期，字符串枚举型【once，day，week，month，year】

<span id="ff_2">**getAlarms():Array&lt;Object&gt;**</span>

<code>获取已设置所有本地通知提醒信息</code>

参数：无

返回值：已设置本地通知信息，数组类型，数组成员为json格式，定义如下：

> id：通知标识，字符串类型
> 
> title：通知标题，字符串类型
> 
> message：通知栏提示内容，字符串类型
> 
> extra：附加字段，json类型
> 
> start：开始时间，数字类型
> 
> circle：循环周期，字符串枚举型【once，day，week，month，year】


<span id="ff_3">**removeAlarm(id:String):void**</span>

<code>删除已设置指定标识本地通知信息</code>

参数：

id：本地通知标识，字符串类型，必选项

返回值：无

<span id="ff_4">**removeAlarms():void**</span>

<code>删除所有已设置本地通知提醒设置</code>

参数：无

返回值：无

<h2 id="cid_2">事件</h2> 

**message**

<code>接收消息触发回调</code>

event事件对象包括：

> type：事件类型，字符串类型，固定值：message；
> 
> target：触发事件的目标组件
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型

param对象为json对象，定义如下：

> id：通知标识，字符串类型
> 
> title：通知栏标题，字符串类型
> 
> message：通知栏提示内容，字符串类型
> 
> extra：附加字段，json类型
> 
> start：开始时间，数字类型
> 
> circle：循环周期，字符串枚举型【once，day，week，month，year】

注：该事件需要在应用入口homeJs中监听

**messageClick**

<code>点击通知消息触发回调</code>

event事件对象包括：
> type：事件类型，字符串类型，固定值：messageClick；
> 
> target：触发事件的目标组件
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型

param对象为json对象，定义如下：
> id：通知标识，字符串类型
> 
> title：通知栏标题，字符串类型
> 
> message：通知栏提示内容，字符串类型
> 
> extra：附加字段，json类型
> 
> start：开始时间，数字类型
> 
> circle：循环周期，字符串枚举型【once，day，week，month，year】

注：该事件需要在应用入口homeJs中监听
