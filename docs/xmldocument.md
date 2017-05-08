# XmlDocument 创建xml对象类

----------

XmlDocument类用于获取xml对象，支持字符串读取和文件读取。



使用时需要在js中引入 ：

```javascript
var xmldocument = require("XmlDocument"); 
```


**注：** 该组件为外置功能组件，打包时候需要选择。

<h2 id="cid_1">js方法</h2>  


<span id="ff_0">**createElementByString(xml: string): XmlElement**</span>  

<code>通过xml文本创建XmlElement对象</code>     

参数：

xml： xml文本数据，字符串类型

返回值：生成的XmlElement对象，若解析失败则返回null



<span id="ff_1">**createElementByFile(xmlFilePath:string):XmlElement**</span>  

<code>读取xml文件创建XmlElement对象</code>   

参数：  

xmlFilePath：xml文件路径，字符串类型，支持本地路径，res: file: 前缀

返回值：生成的XmlElement对象，若解析失败则返回null
