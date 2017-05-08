# NetInfo 网络信息相关类

----------

NetInfo 网络信息相关类主要用于获取手机当前网络状态以及监听网络变化。


使用时需要在js中引入 ：

```javascript
var netinfo = require("NetInfo"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ getStatus(): number  获取当前网络连接状态 ](#ff_0)
> 
> [getIps(): Array&lt;string&gt; 获取连接所有网络ip地址](#ff_1)
> 
>[ getWifiInfo(): Object  获取当前连接的wifi网络信息](#ff_2)




<span id="ff_0">**getStatus(): number**</span>  

<code>获取当前网络连接状态</code>  

参数：无   

返回值：数字枚举型，[0,1,2]  

> 0：设备无网络连接；  
> 
> 1：设备连接方式为WIFI无线网络；
> 
> 2：设备连接方式为移动网络 



<span id="ff_1">**getIps(): Array&lt;string&gt;**</span>  

<code>获取连接所有网络ip地址</code>
 
参数：无  


返回值：数组类型，数组成员为字符串类型



<span id="ff_2">**getWifiInfo(): Object**</span>  

<code>获取当前连接的wifi网络信息</code>   

参数：无  

返回值：Json对象，定义如下：  

> bssId：所连接的wifi的BSSID值，字符串类型，如：bc:54:36:ce:b2:c4
> 
> ssId：所连接wifi设备的名称，字符串类型，如：烽火WIFI路由器1
> 
> ip：连接wifi网络分配的ip地址，字符串类型，如：192.168.95.4





<h2 id="cid_2">事件</h2> 

事件的操作支持以下方法：

> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Function&gt;  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_4)   

**netChanged**  

<code>网络状态改变回调</code>  

event事件对象包括：  

> type：事件类型，字符串类型，固定值：netChanged；
> 
> target：触发事件的目标组件，NetInfo类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param：数字枚举型，[0,1,2]  

> 0：设备无网络连接；
> 
> 1：设备连接方式为WIFI无线网络；
> 
> 2：设备连接方式为移动网络

示例：

```javascript
var net = require("NetInfo");
net.on("netChanged",function(e,status){
     if(status == 0){
        //当前无网络连接 
     }else if(status ==1){
        //当前网络为WIFI
     } else if(status ==2){
        //当前网络为移动网络
     }
});
```