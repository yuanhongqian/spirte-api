# Time 定时器操作类

----------

Time 定时器操作类，主要用于处理定时执行任务，当遇到方法是异步执行的时候，并且要从异步方法里面取变量值，可以用定时器延迟执行任务的时间，保证异步执行的方法执行完成。


使用时需要在js中引入 ：

```javascript
var time = require("Time"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ setTimeout(callFunction:Function,timeout:number): string   启动单次定时器 ](#ff_0)
> 
> [ clearTimeout(id:Time): void  关闭单次定时器 ](#ff_1)
>
>[ setInterval (callFunction:Function,interval:number): string   启动重复定时器  ](#ff_2)
>
> [clearInterval(id:Time): void  关闭重复定时器 ](#ff_3)




<span id="ff_0">**setTimeout(callFunction:Function,timeout:number): string**</span>  

<code>启动单次定时器</code>    

参数：  

callFunction：需要被执行回调函数，函数类型，该回调函数存在入参：  

>  id：定时器标识，字符串类型

timeout：延时时间，数字类型，单位毫秒  

返回值：定时器标识，字符串类型




<span id="ff_1">**clearTimeout(id:Time): void**</span>  

<code>关闭单次定时器</code>

参数：  

id：需要被关闭的定时器标识，字符串类型，必选项  

返回值：无



<span id="ff_2">**setInterval (callFunction:Function,interval:number): string**</span>  

<code>启动重复定时器</code>   

参数：  

callFunction：需要被执行回调函数，函数类型，该回调函数存在入参：  

> id：定时器标识，字符串类型

interval：间隔时间，数字类型，单位毫秒  

返回值：定时器标识，字符串类型


<span id="ff_3">**clearInterval(id:Time): void**</span>  

<code>关闭重复定时器</code>  

参数：  

id：需要被关闭的定时器标识，字符串类型，必选项  

返回值：无