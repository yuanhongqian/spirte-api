# Window 页面操作类

----------

window页面操作类主要用于监听页面的一些事件，并对页面的打开和关闭做一些控制。


使用时需要在js中引入 ：

```javascript
var window = require("Window"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ open(jsonData:Object): void   打开新窗口（通过地址） ](#ff_0)
> 
> [openData(jsonData:Object): void  打开新窗口（通过内容）](#ff_1)
> 
>[ close(jsonData:Object): void  关闭当前窗口  ](#ff_2)
> 
> [getData(): Object  获取上层窗口传递的数据](#ff_3)
> 
> [getOrientation(): string  获取当前窗口屏幕横竖屏状态  ](#ff_4)
> 
>[ getScreenWidth(): number  获取当前窗口绘制区域宽度  ](#ff_5)
> 
> [getScreenHeight(): number  获取当前窗口绘制区域高度  ](#ff_6)
> 
> [setStatusBarMode(mode:string): void   设置窗口状态栏模式](#ff_7)  
> 
>[ hideSip(): void   隐藏系统输入法  ](#ff_8)
>
>[isTop(): boolean 当前窗口是否为顶层窗口](#ff9)




<span id="ff_0">**open(jsonData:Object): void**</span>  

<code>打开新窗口（通过地址）</code>  

参数：  

JsonData：传入打开新窗口参数，Json类型，定义如下：  

> url：需打开uixml页面文件路径，仅支持本地文件，字符串类型，支持res：前缀，必选项；  
> 
> target：开窗方式，字符串枚举型，[_blank,_self]，可选项   
> 
> -   _blank：新窗口打开（默认）
> 
> -   _self：自身窗口打开；   
> 
> id：窗口唯一标识，字符串类型，可选项；  
> 
> data：传递附加参数，支持数字类型，字符串类型，数组类型，JSON类型，新窗口通过getData()方法获取传递参数，可选项；  
> 
> openAnimation：页面开窗动画，字符串枚举型，[slide_l2r, slide_r2l, slide_b2t, slide_t2b, push_l2r, push_r2l,push_b2t,push_t2b,fade,none]可选项
>   
> - slide_l2r：从左至右滑出
> 
> - slide_r2l：从右至左滑出（默认）
> 
> - slide_b2t：从下至上滑出
> 
> - slide_t2b：从上至下滑出
> 
> - push_l2r：从左至右推出
> 
> - push_r2l：从右至左推出
> 
> - push_b2t：从底至上推出
> 
> - push_t2b：从上至底推出
> 
> - fade：淡入淡出
> 
> - none：无动画效果
> 
> closeAnimation：页面关窗动画，字符串枚举型，[slide_l2r, slide_r2l, slide_b2t, slide_t2b, push_l2r, push_r2l,push_b2t,push_t2b,fade,none]，默认采用窗口开窗动画对应的关闭动画，可选项    
 
> - slide_l2r：从左至右滑出
> 
> - slide_r2l：从右至左滑出
> 
> - slide_b2t：从下至上滑出
> 
> - slide_t2b：从上至下滑出
> 
> - push_l2r：从左至右推出
> 
> - push_r2l：从右至左推出
> 
> - push_b2t：从底至上推出
> 
> - push_t2b：从上至底推出
> 
> - fade：淡入淡出
> 
> - none：无动画效果
> 
> statusBar：顶部状态栏显示状态，字符串枚举型，[normal，hide，transparent]   
>   
> - normal：顶部状态栏显示，窗口视图从状态栏下方开始显示（默认）；
> 
> - hide：顶部状态栏隐藏，窗口视图从屏幕最顶端开始显示；
> 
> - transparent：顶部状态栏透明，窗口视图从屏幕最顶端开始显示，透过状态栏看到下方窗口视图，注：android5.0及后续版本支持；
> 
> statusBarColor：状态栏背景色，#rrggbb，默认值transparent透明色，注：android5.0及后续版本支持；
> 
> statusBarMode：状态栏前景模式,字符串枚举型号,【default,light】,iOS及Android 6.0及以上系统支持
> - default：系统状态栏前景色（电池电量、时间、网络部分标识的颜色）为白色
> 
> - light：系统状态栏前景色（电池电量、时间、网络部分标识的颜色）为黑色
> 
> orientation：当前页面横竖屏设置，字符串枚举型，可选项，若不设置则采用程序入口app.json应用配置文件中统一设置，[portrait, landscape,device]  
> 
> - portrait:竖屏
> 
> - landscape:横屏
> 
> - device:支持横竖屏切换
> 
> systemCloseGesture：iOS是否使用系统关窗手势，bool型，可选项，true：使用关窗手势（默认）；false：不使用关窗手势；注：仅iOS支持  

返回值：无



示例：

```javascript
function openpagetest(){
	var jsonData = {};
	jsonData.url = "res:spriteClient/page/newPage.uixml";
	jsonData.target = "_blank";
	
	var jsonObj = {};
	jsonObj.category = "car";
	jsonObj.brand = "BMW";
	jsonData.data = jsonObj;
	
	jsonData.openAnimation = "slide_l2r";
	jsonData.closeAnimation = "slide_r2l";
	jsonData.statusBar = "transparent";
	jsonData.statusBarColor = "#ff0000";
	jsonData.statusBarMode = "light";
	jsonData.orientation = "portrait";
	window.open(jsonData);
}
```

<span id="ff_1">**openData(jsonData:Object): void**</span>  

<code>打开新窗口（通过内容）</code>

参数：  

JsonData：传入打开新窗口参数，Json类型，定义如下：  

> content：需打开uixml页面内容，字符串类型，必选项；  
> 
> target：开窗方式，字符串枚举型，[_blank,_self]，可选项   
> 
> -   _blank：新窗口打开（默认）
> 
> -   _self：自身窗口打开；   
> 
> id：窗口唯一标识，字符串类型，可选项；  
> 
> data：传递附加参数，支持数字类型，字符串类型，数组类型，JSON类型，新窗口通过getData()方法获取传递参数，可选项；  
> 
> openAnimation：页面开窗动画，字符串枚举型，[slide_l2r, slide_r2l, slide_b2t, slide_t2b, push_l2r, push_r2l,push_b2t,push_t2b,fade,none]可选项
>   
> - slide_l2r：从左至右滑出
> 
> - slide_r2l：从右至左滑出（默认）
> 
> - slide_b2t：从下至上滑出
> 
> - slide_t2b：从上至下滑出
> 
> - push_l2r：从左至右推出
> 
> - push_r2l：从右至左推出
> 
> - push_b2t：从底至上推出
> 
> - push_t2b：从上至底推出
> 
> - fade：淡入淡出
> 
> - none：无动画效果
> 
> closeAnimation：页面关窗动画，字符串枚举型，[slide_l2r, slide_r2l, slide_b2t, slide_t2b, push_l2r, push_r2l,push_b2t,push_t2b,fade,none]，默认采用窗口开窗动画对应的关闭动画，可选项    
 
> - slide_l2r：从左至右滑出
> 
> - slide_r2l：从右至左滑出
> 
> - slide_b2t：从下至上滑出
> 
> - slide_t2b：从上至下滑出
> 
> - push_l2r：从左至右推出
> 
> - push_r2l：从右至左推出
> 
> - push_b2t：从底至上推出
> 
> - push_t2b：从上至底推出
> 
> - fade：淡入淡出
> 
> - none：无动画效果
> 
> statusBar：顶部状态栏显示状态，字符串枚举型，[normal，hide，transparent]   
>   
> - normal：顶部状态栏显示，窗口视图从状态栏下方开始显示（默认）；
> 
> - hide：顶部状态栏隐藏，窗口视图从屏幕最顶端开始显示；
> 
> - transparent：顶部状态栏透明，窗口视图从屏幕最顶端开始显示，透过状态栏看到下方窗口视图，注：android5.0及后续版本支持；
> 
> statusBarColor：状态栏背景色，#rrggbb，默认值transparent透明色，注：android5.0及后续版本支持；
> 
> statusBarMode：状态栏前景模式，字符串枚举型号，[default,light] ， 仅iOS支持  
> 
> - default：系统状态栏前景色（电池电量、时间、网络部分标识的颜色）为黑色
> 
> - light：系统状态栏前景色（电池电量、时间、网络部分标识的颜色）为白色
> 
> orientation：当前页面横竖屏设置，字符串枚举型，可选项，若不设置则采用程序入口app.json应用配置文件中统一设置，[portrait, landscape,device]  
> 
> - portrait:竖屏
> 
> - landscape:横屏
> 
> - device:支持横竖屏切换
> 
> systemCloseGesture：iOS是否使用系统关窗手势，bool型，可选项，true：使用关窗手势（默认）；false：不使用关窗手势；注：仅iOS支持  

返回值：无


示例：

```javascript
function openpagetest(){
	var jsonData = {};
	//通过文件读取到页面内容。
	jsonData.content = file.readTextFile("res:spriteClient/page/newPage.uixml");
	jsonData.target = "_blank";
	
	var jsonObj = {};
	jsonObj.category = "car";
	jsonObj.brand = "BMW";
	jsonData.data = jsonObj;
	
	jsonData.openAnimation = "slide_l2r";
	jsonData.closeAnimation = "slide_r2l";
	jsonData.statusBar = "transparent";
	jsonData.statusBarColor = "#ff0000";
	jsonData.statusBarMode = "light";
	jsonData.orientation = "portrait";
	window.open(jsonData);
}
```


<span id="ff_2">**close(jsonData:Object): void**</span>  

<code>关闭当前窗口</code>   

参数：

jsonData：关闭窗口参数设置，可选项，Json对象定义如下：

> data：传递附加参数，支持数字类型，字符串类型，数组类型，JSON类型， 上层页面通过系统事件 "result" 可监听，可选项；

如B页面关闭的时候，向其上层A页面传参时使用。

返回值：无

```javascript
title.on("left_btn_click", function(e) {
  var jsonData = {};
  jsonData.data = "传值到上层页面";
  window.close(jsonData);
});
```

在上层页面中通过：

```javascript
window.on("result",function(e,data){
 //获取前一个页面在页面关闭时候传过来的值。
  var str = data;
});
```

<span id="ff_3">**getData(): Object**</span>  

<code>获取上层窗口传递的数据</code>  

如从A页面打开B页面的时候，并且向B页面传参，可以在B页面通过该方法获取A页面传来的参数值。

参数：无 

返回值：上层窗口传递的数据，支持数字类型，字符串类型，数组类型，JSON类型


<span id="ff_4">**getOrientation(): string**</span>  

<code>获取当前窗口屏幕横竖屏状态</code> 

参数：无  

返回值：设备方向，入参标识设备方向，字符串枚举型，[landscape, portrait]  

> landscape：横屏；
> 
> portrait：竖屏；


<span id="ff_5">**getScreenWidth(): number**</span>  

<code>获取当前窗口绘制区域宽度</code> 

参数：无  

返回值：当前窗口绘制区域宽度，单位dp




<span id="ff_6">**getScreenHeight(): number**</span>  

<code>获取当前窗口绘制区域高度</code> 

参数：无  

返回值：当前窗口绘制区域高度，单位dp


<span id="ff_7">**setStatusBarMode(mode:string): void**</span>  

<code>设置窗口状态栏模式</code> 

参数： 

mode：状态栏前景模式，字符串枚举型号，[default,light],必选项  

> default：系统状态栏前景色（电池电量、时间、网络部分标识的颜色）为白色
> 
> light：系统状态栏前景色（电池电量、时间、网络部分标识的颜色）为黑色  

返回值：无  

注：仅iOS支持


<span id="ff_8">**isTop(): boolean**</span>  

<code>隐藏系统输入法</code>  

参数：无   

返回值：当前窗口是否为顶层窗口,bool类型,

> true：顶层窗口；
> 
> false：非顶层窗口


<span id="ff_9">**hideSip(): void**</span>  

<code>隐藏系统输入法</code>  

参数：无 

返回值：无  


<h2 id="cid_2">事件</h2> 

事件的操作支持以下方法：

> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Function&gt;  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_4)   

本节目录：

[loaded  页面加载完成后触发 ](#sj_1)

[animator  页面开窗动画完毕后触发](#sj_2)  

[resume  页面激活时触发](#sj_3)  

[pause  页面被覆盖时触发](#sj_4)

[destroy  页面被销毁时触发](#sj_5)

[result  接收上层页面关闭回传数据](#sj_6)

<span id="sj_1">**loaded**</span>  

<code>页面加载完成后触发</code>  

event事件对象包括：

> type：事件类型，字符串类型，固定值：loaded；
> 
> target：触发事件的目标组件，window类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

**注：**  虽然该事件是页面加载完成后触发，但是该事件里面的逻辑执行完成之后才会显示界面，如果有大量复杂的逻辑在页面初始化要完成，不建议放在该事件里面执行，否者页面显示出来会比较慢，大量逻辑代码建议放在animator事件里面做处理。

示例：

```javascript
var window = require("Window");
window.on("loaded",function(){

});
```



<span id="sj_2">**animator**</span>  

<code>页面开窗动画完毕后触发</code>  

其执行顺序在loaded之后

event事件对象包括：

> type：事件类型，字符串类型，固定值：animator；
> 
> target：触发事件的目标组件，window；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

**注：** 如果页面加载的时候需要做动画操作，只能放在该事件里面才能生效。 

示例：

```javascript
var window = require("Window");
window.on("animator",function(){

});
```


<span id="sj_3">**resume**</span>  

<code>页面激活时触发</code>  

页面激活的场景主要有：

> 页面刚加载的时候会执行，其执行顺序在loaded之后，由于是异步的和animator基本同时执行没有太严格的执行顺序，建议不要在resume和animator里面做严格逻辑的操作，比如：在一个里面赋值变量，另一个里面获取该变量的值。
> 
> 当前一个窗口页面关闭，本窗口页面显示出来的时候会执行。

event事件对象包括：

> type：事件类型，字符串类型，固定值：resume；
> 
> target：触发事件的目标组件，window；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型


示例：

```javascript
var window = require("Window");
window.on("resume",function(){
});
```

<span id="sj_4">**pause**</span>  

<code>页面被覆盖时触发</code>  

当A页面被B页面覆盖的时候，会执行一次。

event事件对象包括：

> type：事件类型，字符串类型，固定值：pause；
> 
> target：触发事件的目标组件，window；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型



<span id="sj_5">**destroy**</span>  

<code>页面被销毁时触发</code>   

event事件对象包括： 

> type：事件类型，字符串类型，固定值：destroy；
> 
> target：触发事件的目标组件，window类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型 


<span id="sj_6">**result**</span>  

<code>接收上层页面关闭回传数据</code>   

event事件对象包括： 

> type：事件类型，字符串类型，固定值：result；
> 
> target：触发事件的目标组件，window类；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型 

param： 可为数字类型/字符串类型/数组类型/JSON类型格式；