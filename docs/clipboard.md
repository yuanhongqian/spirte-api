# Clipboard 系统剪切板读取类

----------

Clipboard 系统剪切板读取类，该缓存数据可用于设备不同程序间共享数据。


使用时需要在js中引入 ：

```javascript
var clipboard = require("Clipboard"); 
```

**注：** 该组件为外置功能组件，打包需要选择此功能。

<h2 id="cid_1">js方法</h2>  


<span id="ff_0">**setData(value:string): void**</span>  

<code>设置程序剪切板</code>    

参数：  

value：存入数据value值，字符串类型；  

返回值：无



示例：

```javascript
//页面存入数据操作
var clipboard = require("Clipboard");
//存入数据
clipboard.setData("Sprite");
```




<span id="ff_1">**getData(): string**</span>  

<code>读取程序剪切板</code>

参数：无 


返回值：存入数据value值，字符串，若获取失败则返回null；

示例：

```javascript
var clipboard = require("Clipboard");
var str = clipboard.getData();
````

