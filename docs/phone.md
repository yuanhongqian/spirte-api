# Phone 电话操作类

----------

 Phone 电话操作类主要用于拨打电话，启动系统拨号界面，获取通话记录等功能。

使用时需要在js中引入 ：

```javascript
var phone = require("Phone"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ tel(phone:string): void  拨打指定号码 ](#ff_0)
> 
> [openSystemDial(phone:string): void  启动系统拨号界面 ](#ff_1)
> 
> [faceTime(faceTimeNumber:string): void   调用IOS平台系统的FaceTime进行视频通话 ](#ff_2)
> 
> [getCallRecords(jsonData:Object,callBackFun:Function): void    获取系统通话记录 ](#ff_3)
> 

<span id="ff_0">**tel(phone:string): void **</span>  

<code>拨打指定号码</code>     

参数：  

phone：需要拨打电话号码，字符串类型，必选项；  

返回值：无



<span id="ff_1">**openSystemDial(phone:string): void**</span>  

<code>启动系统拨号界面</code>   

参数：  

phone：需要预制的电话号码，字符串类型，可选项 

返回值：无  

**注：** 仅Android支持


<span id="ff_2">**faceTime(faceTimeNumber:string): void**</span>  

<code>调用IOS平台系统的FaceTime进行视频通话</code> 

参数:  

faceTimeNumber：进行视频通话的号码，字符串类型，必选项，当使用手机时，该号码是对方的电话号码，当使用ipod /touch/ipad，该号码是对方的itunes账号

返回值：无  

**注：** 仅iOS平台支持


<span id="ff_3">**getCallRecords(jsonData:Object,callBackFun:Function): void**</span>  

<code>获取系统通话记录</code>  


参数: 

jsonData：获取系统通话记录传入参数，Json对象定位如下：  

> type：电话记录类型，数字，必选项，[0,1,2,3,4]
> 
> - 0：所有类型；
> 
> - 1：拨出未接通；
> 
> - 2：拨出已接通；
> 
> - 3：拨入已接通；
> 
> - 4：拨入未接通； 

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：获取通话记录成功；
> 
> - -1：获取通话记录失败；
> 
> datas：数组类型，数组中每项为Json对象，定义如下：
> 
> - type：电话记录类型，数字，[0,1,2,3,4]
>   -  0：所有类型；
>   -  1：拨出未接通；
>   - 2：拨出已接通；
>   - 3：拨入已接通；
>   - 4：拨入未接通； 
> 
> - number：电话号码，字符串类型；
> 
> - name：电话号码对应的手机通讯录联系人名称，字符串类型；
> 
> - startTime：拨出或拨入开始时间 字符串，输出格式为yyyy-mm-dd hh:mm:ss；
> 
> - endTime：拨出或拨入结束时间，字符串类型，输出格式为yyyy-mm-dd hh:mm:ss；
> 
> - duration：通话时长，数字类型，单位秒

返回值：无  

**注：** 仅Android支持
