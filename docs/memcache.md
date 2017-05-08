# MemCache 内存缓存读取类

----------

MemCache 内存缓存读取类，该缓存程序运行过程中生效，程序关闭则自动清空。


使用时需要在js中引入 ：

```javascript
var memcache = require("MemCache"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ setItem(key:string,value:any): void  内存缓存数据 ](#ff_0)
> 
> [getItem(key:string): any  读取内存缓存数据 ](#ff_1)
>
>[ removeItem(key:string): any   移除内存缓存数据  ](#ff_2)



<span id="ff_0">**setItem(key:string,value:any): void**</span>  

<code>内存缓存数据</code>    

参数：  

> key：存入数据key值，字符串类型；
> 
> value：存入数据value值，支持数字，字符串，数组，JSON类型；  

返回值：无


示例：

```javascript

//页面存入数据操作
var memCache = require("MemCache");
//存入数字
memCache.setItem("key1",22.5);
//存入字符串
memCache.setItem("key2", "Sprite");
//存入数组
memCache.setItem("key3", [ "姓名", "电话", "日期" ]);
//存入JSON
memCache.setItem("key4", {
        "k1" : "v1",
        "k2" : "v2",
        "k3" : "v3",
        "k4" : "v4"
});
```




<span id="ff_1">**getItem(key:string): any**</span>  

<code>读取内存缓存数据</code>

参数：  

key：读取数据key值，字符串类型；  

返回值：存入数据value值，支持数字，字符串，数组，JSON类型，若获取失败则返回null

示例：

```javascript

var memCache = require("MemCache");
//读取数字 
var num = memCache.getItem("key1");
//读取字符串
var str = memCache.getItem("key2");
//读取数组
var arr = memCache.getItem("key3");
var value1 = arr[1];
//读取JSON
var jso = memCache.getItem("key4");
var value2 = jso.k1;
```

<span id="ff_2">**removeItem(key:string): any**</span>  

<code>移除内存缓存数据</code>   

参数：  

key：需移除数据key值，字符串类型；  

返回值：已移除的数据value值，支持数字，字符串，数组，JSON类型，若获取失败则返回null；

