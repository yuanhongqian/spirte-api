# Document 页面Dom操作类

----------

Document页面Dom操作类，主要用于控制布局页面组件dom，包括创建，添加，移除，刷新等功能。


使用时需要在js中引入 ：

```javascript
var document = require("Document"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ getElement(id:string): IElement  根据Id获取页面内UI控件对象 ](#ff_0)
> 
> [ getElements(rule:string): Array&lt;IElement&gt;  根据特定规则获取页面内UI控件对象集 ](#ff_1)
> 
>[ getRootElement(): IElement  获取页面根对象  ](#ff_2)
> 
> [createElement(tagName:string,propsData:Object,domObj:IElement): IElement  创建UI控件对象 ](#ff_3)
> 
> [createElementByXml(xml:string,domObj:IElement):IElement  通过xml文本创建UI控件对象  ](#ff_4)
> 
>[ refresh(): void  刷新页面Dom树  ](#ff_5)
> 
>[ getPathLocation(): string  获取本页面所在目录路径  ](#ff_6)




<span id="ff_0">**getElement(id:string): IElement**</span>  

<code>根据Id获取页面内UI控件对象</code>  

参数：  

id：UI组件的唯一标识，字符串类型；

返回值：控件dom对象，若查找失败则返回null


<span id="ff_1">**getElements(rule:string): Array&lt;IElement&gt;**</span>  

<code>根据特定规则获取页面内UI控件对象集</code>

参数：  

rule：查询规则，字符串类型，支持多规则同时匹配取合集，不同规则直接以,分割，支持规则包括：  

> 类型选择器：如button
> 
> ID选择器： 如 #submit
> 
> 类选择器： 如 .login
> 
> 属性选择器[att="val"）：如 [type="text"]
 
返回值：数组，数组成员为控件dom对象，若查找失败则返回length为0的空数组  


示例：

```javascript
var document = require("Document");  

var rule = 'button,#submit,.login, [type="login"]';
var arrayObj = document.getElements (rule);
if(arrayObj.length != 0){
   //执行后续操作
}else{
  //无法找到匹配元素
}

```


<span id="ff_2">**getRootElement(): IElement**</span>  

<code>获取页面根对象</code>   

参数：无  

返回值：控件dom对象，若查找失败则返回null

示例：

```javascript
var document = require("Document");
var rootObj = document.getRootElement();
if(rootObj !=null){
   //执行后续操作
}else{
}
```


<span id="ff_3">**createElement(tagName:string,propsData:Object,domObj:IElement): IElement**</span>  

<code>创建UI控件对象</code>  

参数：  

tagName：需要创建的UI控件对象名，字符串类型，必选参数；  

propsData：创建UI控件对象传入属性集，Json类型，可选参数，key为属性名，value为属性值；  

domObj：当前js运行环境对象，可选参数，component模板中使用，传入this即可；  

返回值：创建生成dom对象，若创建失败则返回null


**注：**  创建完后需要刷新布局控件才能显示，如果局部区域大小固定，建议用局部刷新。

示例：

```javascript

var rootDom = document.getRootElement();
var json = {};
//创建样式属性
json.style = "background-color:black;width:fill_screen;height:fill_screen;position:absolute;top:0;left:0;opacity:0.5";
//创建id属性
json.id="box_1";
//创建自定义属性
json.abc="abc";

//创建一个box
var backGroundDom = document.createElement("box", json);
rootDom.appendChild(backGroundDom);
document.refresh();
```





<span id="ff_4">**createElementByXml(xml:string,domObj:IElement):IElement**</span>  

<code>通过xml文本创建UI控件对象</code> 

参数：  

xml： xml文本数据  

domObj：当前js运行环境对象，可选参数，component模板中使用，传入this即可；

返回值：创建生成dom对象，若创建失败则返回null


**注：**  创建完后需要刷新布局控件才能显示，如果局部区域大小固定，建议用局部刷新。

示例：

```javascript

var popxmlstr = '<box id="box_1" ><text>123</text></box>';
//创建一个box
var popmenu= document.createElementByXml(popxmlstr:string): Object;
popbgid.appendChild(popmenuobj);  
document.refresh();
```


<span id="ff_5">**refresh(): void**</span>  

<code>刷新页面Dom树</code> 

参数：无  

返回值：无  

**注：**  当Element对象属性或者CSS更新完毕后(布局区域发生变化时，如高宽改变)，调用该函数刷新至系统UI界面。该方法在android上有效率问题，建议尽量少用，多用局部刷新。



<span id="ff_6">**getPathLocation(): string**</span>  

<code>获取本页面所在目录路径</code>  

使用场景：一般在做组件模板封装的时候会用到，比如模板里面定义的组件需要传入图片，但是又希望图片的路径是基于uixml页面的相对路径，可以在模板里面通过该方法得到uixml的绝对路径，然后和相对路径进行拼接，保证使用者传入的图片路径是基于uixml的相对路径。注： 模板内部的相对路径是基于模板文件的相对路径（保证模板的封装性）。

参数：无  

返回值：本页面所在目录路径，res:前缀，，字符串类型

示例：  

```javascript
var  pathLocation = document.getPathLocation();
```

**注：**  如果在组件模板页面里面，想获取模板页面的目录路径，需要用this.getPathLocation()
