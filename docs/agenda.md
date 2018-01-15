# Agenda 系统日程

----------


Agenda系统日程工具类，操作系统日程相关。


使用时需要在js中引入 ：

```javascript
var agenda = require("Agenda"); 
```

**注：** 该组件为外置功能组件。

<h2 id="cid_1">js方法</h2>

本节目录：

> [addAgendaUser(jsonData:Object,callbackFun:Function): void  往系统日历添加账户](#ff_1)
> 
> [getAgendaUser(id:String): Object  获取系统日历账户 ](#ff_2) 
> 
> [removeAgendaUser(id:String): void  删除已添加的系统日历账户，同时会删除该用户所有日程](#ff_3)
> 
> [addAgenda(jsonData:Object,callbackFun:Function): void  添加系统日程](#ff_4)
> 
>  [getAgenda(id:String): Object  获取已设置日程信息](#ff_5)
> 
>  [getAgendasByUser(userId:String):Array&lt;Object&gt;  获取某用户已设置的所有日程信息 ](#ff_6)
> 
>  [removeAgenda(id:String): void  删除已设置指定标识系统日程信息 ](#ff_7)
> 
>  [removeAgendasByUser(userId:String):void  删除某用户所有已设置的系统日程信息 ](#ff_8)






<span id="ff_1">**addAgendaUser(jsonData:Object，callbackFun:Function): void**</span>  

<code>往系统日历添加账户</code>  

参数：  

jsonData：系统日历添加账户传入参数，json类型，必选项，定义如下：

> name：账户名，字符串类型，必选项；
> 
> email：邮箱，字符串类型，必选项，仅Android支持；

callFunction：操作回调函数，函数具有json类型入参，定义如下：

> code：回应状态码，数字【0，-1】。0：插入账户成功；-1：插入账户失败；
> 
> userId：成功插入账户后返回的账户id，用于以后插入日程或查询账户，字符串类型

返回值：无



<span id="ff_2">**getAgendaUser(id:String): Object**</span>  

<code>获取系统日历账户</code> 

参数：

userId：账户id，字符串类型，必选项

返回值：已设置账户信息，json格式，定义如下：

> code：回应状态码，0：获取账户成功；-1：获取账户失败
> 
> name：账户名，字符串类型；
> 
> email：邮箱，字符串类型，仅Android支持




<span id="ff_3">**removeAgendaUser(id:String): void**</span>  

<code>删除已添加的系统日历账户，同事会删除该用户所有日程</code>    

参数：

id：账户id，字符串类型，必选项

返回值：无



<span id="ff_4">**addAgenda(jsonData:Object,callbackFun:Function): void**</span>  

<code>添加系统日程</code>  

参数：

jsonData：设置系统日程提醒传入参数，json类型，必选项，定义如下：

> userId：要插入日程的账户id，必选项；
> 
> title：日程标题，字符串类型，必选项；
> 
> start：开始时间，数字类型，单位毫秒，设置的日期和时间距1970年1月1日午夜之间的毫秒数，必选项
> 
> end：结束时间，数字类型，单位毫秒，设置的日期和时间距1970年1月1日午夜之间的毫秒数，必选项；
> 
> circle：循环周期，字符串枚举型【once，day，week，month，year】，可选项
> 
> - once：仅一次，不重复；默认
> 
> - day：每天重复；
> 
> - week：每周重复，如设置日程提醒为周二 15:30，则后续周周二 15:30均进行提醒；
> 
> - month：每月重复，如设置日程提醒日期为8月6日 15:30，则后续月份6日 15:30均进行提醒；
> 
> - year： 每年重复，如设置日程提醒日期为8月6日 15:30，则下年8月6日 15:30均进行提醒
> 
> description：日程备注，字符串类型，可选项
> 
> eventLocation：日程发生地点，字符串类型，可选项；
> 
> isAlarm：是否提醒，boolean型，可选项，默认为true；
> 
> alarmMinutes：提醒的时间，数字类型，单位为分钟，可选项，
> - -1：不提醒；
> 
> - 0：日程开始前（默认）；
> 
> - 其他：日程前几分钟提醒，如设置5，则表示日程开始5分钟前提醒

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：设置系统日程成功；-1：设置系统日程失败；
> 
> id：成功设置的日程编号，字符串类型

返回值：无 



<span id="ff_5">**getAgenda(id:String): Object**</span>  

<code>获取已设置日程信息</code> 

参数：

id：日程id，字符串类型，必选项

返回值：已设置日程信息，json格式，定义如下：

> userId：日程的账户id，字符串类型
> 
> id：日程标识，字符串类型
> 
> title：日程标题，字符串类型
>
> start：开始时间，数字类型
>
> end：结束时间，数字类型
>
> circle：循环周期，字符串枚举型[once, day, week, month, year]
> 
> description：日程备注，字符串类型
>
> eventLocation：日程发生地点，字符串类型
>
> isAlarm：是否提醒，boolean型，
>
> alarmMinutes：提醒的时间，数字类型，单位为分钟




<span id="ff_6">**getAgendasByUser(userId:String):Array&lt;Object&gt;**</span>  

<code>获取某用户已设置的所有日程信息</code> 

参数：

userId：账户id，字符串类型，必选项

返回值：已设置日程信息，数组类型，数组成员为json格式，定义如下：

> userId：日程的账户id，字符串类型
> 
> id：日程标识，字符串类型
> 
> title：日程标题，字符串类型
> 
> start：开始时间，数字类型
> 
> end：结束时间，数字类型
> 
> circle：循环周期，字符串枚举型[once,day,week,month,year]
> 
> description：日程备注，字符串类型
> 
> eventLocation：日程发生地点，字符串类型
> 
> isAlarm：是否提醒，boolean型
> 
> alarmMinutes：提醒的时间，数字类型，单位为分钟




<span id="ff_7">**removeAgenda(id:String): void**</span>  

<code>删除已设置指定标识系统日程信息</code> 

参数：

id：设置日程提醒标识，字符串类型，必选项

返回值：无



<span id="ff_8">**removeAgendasByUser(userId:String):void**</span>  

<code>删除某用户所有已设置的系统日程信息</code>  

参数：

userId：用户账号id，字符串类型，必选项

返回值：无

	






