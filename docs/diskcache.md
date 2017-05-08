# DiskCache 磁盘缓存读取类

----------

DiskCache 磁盘缓存读取类，该缓存数据以文件格式持久化保存。


使用时需要在js中引入 ：

```javascript
var diskcache = require("DiskCache"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ setItem(key:string,value:any): void  磁盘缓存数据 ](#ff_0)
> 
> [getItem(key:string): any  读取磁盘缓存数据 ](#ff_1)
>
>[ removeItem(key:string): any   移除磁盘缓存数据  ](#ff_2)



<span id="ff_0">**setItem(key:string,value:any): void**</span>  

<code>磁盘缓存数据</code>    

参数：  

> key：存入数据key值，字符串类型；
> 
> value：存入数据value值，支持数字，字符串，数组，JSON类型；  

返回值：无


示例：

```javascript

//页面存入数据操作
var diskCache = require("DiskCache");
//存入数字
diskCache.setItem("key1",22.5);
//存入字符串
diskCache.setItem("key2", "Sprite");
//存入数组
diskCache.setItem("key3", [ "姓名", "电话", "日期" ]);
//存入JSON
diskCache.setItem("key4", {
        "k1" : "v1",
        "k2" : "v2",
        "k3" : "v3",
        "k4" : "v4"
});

```

<span id="ff_1">**getItem(key:string): any**</span>  

<code>读取磁盘缓存数据</code>

参数：  

key：读取数据key值，字符串类型；  

返回值：存入数据value值，支持数字，字符串，数组，JSON类型，若获取失败则返回null

示例：

```javascript

var diskCache = require("DiskCache");
//读取数字 
var num = diskCache.getItem("key1");
//读取字符串
var str = diskCache.getItem("key2");
//读取数组
var arr = diskCache.getItem("key3");
var value1 = arr[1];
//读取JSON
var jso = diskCache.getItem("key4");
var value2 = jso.k1;

````

<span id="ff_2">**removeItem(key:string): any**</span>  

<code>移除磁盘缓存数据</code>   

参数：  

key：需移除数据key值，字符串类型；  

返回值：已移除的数据value值，支持数字，字符串，数组，JSON类型，若获取失败则返回null；

<span id="ff_3">**clear(): void**</span>  

<code>清空磁盘缓存数据</code>   

参数：无  

返回值：无

