# 公共方法

----------
  
<h2 id="cid_0">事件相关</h2>

本节目录：  
> 
> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Object&gt; 获取已绑定的事件的触发函数](#jjxg_4)   


<span id="jjxg_1">**on(messageName:string,callback:Function): void**</span>

<code> 组件注册事件的触发函数</code>

参数：  

messageName：注册消息标识，字符串类型，必选项；

callback：绑定回调触发函数，函数类型，必选项，函数入参定义如下：

> event：事件类型，Event对象，定义包括：
> 
> -  type：消息标识，字符串类型；
> 
> -  target：触发事件的目标组件，dom对象；
> 
> -  timestamp：事件触发的时间戳,单位毫秒，数字类型 
> 
> param：可变参数，根据fire触发传参来定；

返回值：无

示例：   

```javascript
//注册系统点击事件
button.on("click", function (event) {
    var eventType = event.type;
    var targetObj = event.target;
    var timestamp = event.timestamp;
});
//注册自定义事件
button.on("login", function (event, param1, param2) {
    var eventType = event.type;
    //获取传递参数1
    var p1 = param1;
    //获取传递参数2
    var p2 = param2;
});

```


<span id="jjxg_2">**fire(messageName:string,params:Array&lt;any&gt;): void**</span>

<code>组件事件的触发函数</code>

参数：   

messageName：注册消息标识，字符串类型，必选项；  

params：需要传递的参数集，数组类型，可选项；  

返回值：无

示例：  

```javascript
//无参数事件触发 
button.fire("click");
//带参数事件触发
var params = new Array();
params.push("George");
params.push("John");
//params 是数组，这里传递了2个参数给login事件，接受参数参考上面on的示例
button.fire("login", params);
``` 

<span id="jjxg_3">**off(messageName:string,callback:Function): void** </span>

<code>组件移除事件的触发函数</code>  

参数：  

messageName：注册消息标识，字符串类型，必选项；  

callback：指定移除回调触发函数，函数类型，可选项；

返回值：无  

**注：** 若不指定移除函数，则移除组件所有注册 "事件名" 的触发函数；

示例：

```javascript
 //移除所有事件触发 
button.off("click");

//移除指定函数事件触发 
button.off("click",onButtonClick);
function onButtonClick(){
//函数触发
}
```  

<span id="jjxg_4">**getOn(messageName:string): Array&lt;Object&gt;**</span>  

<code>获取已绑定的事件的触发函数</code>  

参数：  

messageName：注册消息标识，字符串类型，必选项；  

返回值：返回消息已绑定的函数集，数组类型，数组成员为函数类型    

**注：** 若消息未绑定触发函数则返回空数组

示例：

```javascript
var eventarr = boxObj.getOn("click");
```  
  

<h2 id="cid_1">动画相关</h2>

本节目录：  
> 
> [startAnimation(jsonData:Object,callback:Function): void  启动UI组件动画](#dhxg_1)   
> 
> [startAnimator(jsonData:Object,callback:Function): void  启动UI组件属性动画](#dhxg_2)   
> 
> [startKeyFrameAnimator(jsonData:Object,callback:Function): void  启动UI组件关键帧动画](#dhxg_3)  
>  
> [releaseAnimator(): void 结束控件动画](#dhxg_4)   

<span id="dhxg_1">**startAnimation(jsonData:Object,callback:Function): void**</span>

<code>启动UI组件动画</code>   

参数：  

jsonData：组件动画定义，Json类型 ，json属性如下：

> fillAfter：动画结束时UI组件是否停留在最后一帧，可选项，数字枚举型，【0,1】 
> 
> -  0：动画结束恢复原始状态（默认）； 
> 
> -  1：动画结束停留在最后一帧；
> 
> pivotX：缩放/旋转动画时设置起点x轴起点位置，取值0 - 1，可选项；
> 
> pivotY：缩放/旋转动画时设置起点y轴起点位置，取值0 - 1，可选项；
> 
> animationSet：组件动画定义，Json数组格式，必选项，动画包括：opacity透明度动画，transfer位移动画，scale缩放动画，rotate旋转动画四种类型，Json参数定义如下：

** 注：**   

- pivotX，pivotY 设置的是位置比例，比如pivotX=0;pivotY=0 表示的控件左上角顶点位置；pivotX=0;pivotY=0.5 表示控件左侧Y轴中间位置；pivotX=0.5;pivotY=0.5标示控件中心点位置（默认就是该位置）；

- animationSet存放的是动画json数组，如果有多种动画同时执行，定义各种动画的json数据，存放在animationSet数组里即可。


animationSet数组格式中各个动画Json属性定义如下：  

【opacity透明度动画】，json属性如下：  

> type：动画类型，字符串，固定为"opacity";  
> 
> delay：动画延迟时间，数字类型，单位毫秒；  
> 
> duration：动画过渡时间，数字类型，单位毫秒；  
> 
> curve：动画速率，字符串枚举型，【ease_in, ease_out, ease_in_out, linear】   
>  
> - ease_in：动画启动的时候慢；
> 
> - ease_out：动画结束的时候慢；
> 
> - ease_in_out：动画启动时候慢，中间快，结束的时候慢；
> 
> - linear动画速度不变（默认）；  
> 
> from：动画开始起始透明值，数字类型，取值0-1，0表示透明，1标识不透明；  
> 
> to：动画结束透明值，数字类型，取值0-1，0表示透明，0表示透明，1标识不透明；  

示例：  

```javascript
var = {};
jsonData.fillAfter = 0;
var animationSet = new Array(): Object;
var opacityAni = {};
opacityAni.type = "opacity";
opacityAni.delay = 1000;
opacityAni.duration = 1000;
opacityAni.curve = "ease_out";
opacityAni.from = 0;
opacityAni.to = 1;
animationSet.push(opacityAni);

jsonData.animationSet = animationSet;

//启动动画
button.startAnimation(jsonData,function(code){
//动画结束后，回调里面做处理
});

```

【transfer位移动画】，json属性如下： 

> type：动画类型，字符串，固定为"transfer";  
> 
> delay：动画延迟时间，数字类型，单位毫秒；
> 
> duration：动画过渡时间，数字类型，单位毫秒；
> 
> curve：动画速率，字符串枚举型，【ease_in, ease_out, ease_in_out, linear】
> 
> - ease_in：动画启动的时候慢；
> 
> - ease_out：动画结束的时候慢；
> 
> - ease_in_out：动画启动时候慢，中间快，结束的时候慢；
> 
> - linear动画速度不变（默认）；
> 
> fromX：起始x坐标； 
> 
> fromY：起始y坐标；  
> 
> toX：结束x坐标；  
> 
> toY：结束y坐标；  

示例： 

```javascript
var = {};
jsonData.fillAfter = 0;
var animationSet = new Array(): Object;

var transferAni = {};
transferAni.type = "transfer";
transferAni.delay = 0;
transferAni.duration = 1000;
transferAni.curve = "ease_out";
transferAni.fromX = 0;
transferAni.toX = 100;
transferAni.fromY = 0;
transferAni.toY = -100;
animationSet.push(transferAni);

jsonData.animationSet = animationSet;

//启动动画
button.startAnimation(jsonData,function(code){
//动画结束后，回调里面做处理
});

```


【scale缩放动画】，json属性如下：  

> type：动画类型，字符串，固定为"scale"; 
> 
> delay：动画延迟时间，数字类型，单位毫秒；
> 
> duration：动画过渡时间，数字类型，单位毫秒；
> 
> curve：动画速率，字符串枚举型，【ease_in, ease_out, ease_in_out, linear】
> 
> - ease_in：动画启动的时候慢；
> 
> - ease_out：动画结束的时候慢；
> 
> - ease_in_out：动画启动时候慢，中间快，结束的时候慢；
> 
> - linear动画速度不变（默认）；
> 
> scaleFromX：起始x的伸缩比例；
> 
> scaleFromY：起始y的伸缩比例；
> 
> scaleToX：结束x的伸缩比例；
> 
> scaleToY：结束y的伸缩比例；


示例： 

```javascript
var = {};
jsonData.fillAfter = 0;
var animationSet = new Array(): Object;

var scaleAni = {};
scaleAni.type = "scale";
scaleAni.delay = 0;
scaleAni.duration = 1000;
scaleAni.curve = "ease_out";
scaleAni.scaleFromX = 1;
scaleAni.scaleToX = 2;
scaleAni.scaleFromY = 1;
scaleAni.scaleToY = 2;
animationSet.push(scaleAni);

jsonData.animationSet = animationSet;

//启动动画
button.startAnimation(jsonData,function(code){
//动画结束后，回调里面做处理
});

```


【rotate旋转动画】 ，json属性如下：

> type：动画类型，字符串，固定为"rotate";
> 
> delay：动画延迟时间，数字类型，单位毫秒；
> 
> duration：动画过渡时间，数字类型，单位毫秒；
> 
> curve：动画速率，字符串枚举型，【ease_in, ease_out, ease_in_out, linear】
> 
> - ease_in：动画启动的时候慢；
> 
> - ease_out：动画结束的时候慢；
> 
> - ease_in_out：动画启动时候慢，中间快，结束的时候慢；
> 
> - linear动画速度不变（默认）；
> 
> fromDegree：起始旋转角度，数字；
> 
> toDegree：结束旋转角度，数字；


示例：  


```javascript  
var = {};
//这里设置从右下角旋转
jsonData.pivotX = 1;
jsonData.pivotY = 1;
jsonData.fillAfter = 0;
var animationSet = new Array(): Object;

var rotateAni = {};
rotateAni.type = "rotate";
rotateAni.duration = 1000;
rotateAni.curve = "ease_out";
rotateAni.fromDegree = 0;
rotateAni.toDegree = 180;
animationSet.push(rotateAni);

jsonData.animationSet = animationSet;

//启动动画
button.startAnimation(jsonData,function(code){
//动画结束后，回调里面做处理
});  

```   

callback：组件动画结束回调函数，可选参数，入参为Json对象，定义如下：  

> code：回应状态码，数字【0,-1】  
> 
> -  0：执行动画成功；
> 
> - -1：执行动画失败；

返回值：无

**注：**  该方法仅做动画效果，并不涉及UI组件真实属性变化，如果不设置fillAfter=1，那么该方法做完动画后，直接还原。 

示例：  

```javascript

//多种动画组合
var = {};
//这里设置从右下角旋转
jsonData.pivotX = 1;
jsonData.pivotY = 1;
jsonData.fillAfter = 0;
var animationSet = new Array(): Object;
//缩放动画
var scaleAni = {};
scaleAni.type = "scale";
scaleAni.delay = 0;
scaleAni.duration = 1000;
scaleAni.curve = "ease_out";
scaleAni.scaleFromX = 1;
scaleAni.scaleToX = 2;
scaleAni.scaleFromY = 1;
scaleAni.scaleToY = 2;
animationSet.push(scaleAni);
//旋转动画
var rotateAni = {};
rotateAni.type = "rotate";
rotateAni.duration = 1000;
rotateAni.curve = "ease_out";
rotateAni.fromDegree = 0;
rotateAni.toDegree = 180;
animationSet.push(rotateAni);

jsonData.animationSet = animationSet;
//启动动画
button.startAnimation(jsonData,function(code){
//动画结束后，回调里面做处理
});

```  

<span id="dhxg_2">**startAnimator(jsonData:Object,callback:Function): void**</span>  

<code>启动UI组件属性动画</code>  

参数：  

jsonData：组件属性动画设置对象，json类型，定义如下：  

> animators：动画集数组，动画顺序执行，数组中每个成员均为json对象，必选项；

**注：** animators组数中动画会按照数组顺序依次执行。

animators中 json属性定义如下：  

> delay：动画延迟时间，数字类型，单位毫秒；
> 
> duration：动画过渡时间，数字类型，单位毫秒；
> 
> curve：动画速率，字符串枚举型，【ease_in, ease_out, ease_in_out, linear】  
> 
> - ease_in：动画启动的时候慢；
> 
> - ease_out：动画结束的时候慢；
> 
> - ease_in_out：动画启动时候慢，中间快，结束的时候慢；
> 
> - linear动画速度不变（默认）；
> 
> pivotX：缩放/旋转动画时设置起点x轴起点位置，取值0 - 1，可选项；；
> 
> pivotY：缩放/旋转动画时设置起点y轴起点位置，取值0 - 1，可选项；
  
> props：需要修改的属性动画值，Json对象，属性定义如下：  
> 
> - x：控件左上角X轴坐标，数字；
> 
> - y：控件左上角Y轴坐标，数字；
> 
> - translationX：控件X轴方向位移，数字；
> 
> - translationY：控件Y轴方向位移，数字；
> 
> - scaleX：控件X轴方向缩放比例，数字；
> 
> - scaleY：控件Y轴方向缩放比例，数字；
> 
> - rotation：控件Z轴旋转角度，数字；
> 
> - rotationX：控件X轴旋转角度，数字；
> 
> - rotationY：控件Y轴旋转角度，数字；
> 
> - opacity：控件透明度设置，数字，取值，[0,1]；
> 
> - backgroundColor：背景色设置，字符串类型，#rrggbbaa，red、yellow等，可以用rgba(0, 0, 0, 0.5)方式来设置。  

**注：** 如果需要组合动画同时执行，都设置在props里面即可。

callback：组件动画结束回调函数，可选参数，入参为Json对象，定义如下：  

> code：回应状态码，数字【0,-1】
> 
> -   0：执行动画成功；
> 
> -  -1：执行动画失败； 

返回值：无

**注：** 

- 该方法调用会引起UI组件真实属性变化，不过如果动画结束后调用releaseAnimator()方法释放动画，并执行document.refresh()，动画会全部还原。 如果希望后续有document.refresh()操作继续刷新组件，有不希望组件动画还原，可以在动画结束的回调函数里面通过setStyle方式，修改其style样式，这样控件就永远固定在动画结束位置了。
 
- 属性动画开始后，组件会受到动画的保护，如果在没有releaseAnimator()释放动画前，组件是不会被document.refresh()刷新的。

示例：

```javascript

//示例中，两个动画会按照先后顺序执行，其中动画一里面是组合动画

var = {};
var aniAry = new Array(): Object;
//第一个动画，同时做缩放和旋转动画
var jsonAni1 = {};
jsonAni1.delay = 0;
jsonAni1.duration = 1000;
jsonAni1.curve = "linear";
jsonAni1.props = {};
jsonAni1.props.scaleX = 0.5;
jsonAni1.props.scaleY = 0.5;
jsonAni1.props.rotation = 350;
jsonAni1.props.y = 150;
jsonAni1.props.x = 200;
aniAry.push(jsonAni1);

//第二个动画，做背景色动画
var jsonAni2 = {};
jsonAni2.delay = 0;
jsonAni2.duration = 1000;
jsonAni2.curve = "ease_out";
jsonAni2.props = {};          
jsonAni2.props.backgroundColor = "rgba(0, 0, 0, 0.5)"; 
aniAry.push(jsonAni2);
jsonData.animators = aniAry;
testBtn.startAnimator(jsonData, function(code){

});
```

<span id="dhxg_3">**startKeyFrameAnimator(jsonData:Object,callback:Function): void**</span>  

<code>启动UI组件关键帧动画</code>    


参数：  

jsonData：组件关键帧动画设置对象，json类型，定义如下：  

> type：关键帧动画类型，包括【translationX, translationY,scaleX,scaleY,scale,rotate, rotationX , rotationY,opacity, backgroundColor】  
> 
> duration：动画过渡时间，数字类型，单位毫秒；
> 
> settings：关键帧设置，顺序执行，数组类型：



settings数组中每个成员均为json对象，定义如下：


> value：动画关键帧设置，不同type，value值对应如下；
> 
> - translationX：控件X轴方向位移，数字；
> 
> - translationY：控件Y轴方向位移，数字；
>  
> - scaleX：控件X轴方向缩放比例，数字；
>  
> - scaleY：控件Y轴方向缩放比例，数字；
>  
> - scale：控件缩放比例，数字；
>  
> - rotation：控件Z轴旋转角度，数字；
>  
> - rotationX：控件X轴旋转角度，数字；
>  
> - rotationY：控件Y轴旋转角度，数字；
>  
> - opacity：控件透明度设置，数字，取值，[0,1]；
>  
> - backgroundColor：背景色设置，字符串类型，#rrggbbaa；
> 
> keyTimes：到关键帧时指定时间点比例，数字类型，0-1之间；
>  
> curve：动画速率，字符串枚举型，【ease_in, ease_out, ease_in_out, linear】
> 
> -  ease_in：动画启动的时候慢；
> 
> -  ease_out：动画结束的时候慢；
> 
> -  ease_in_out：动画启动时候慢，中间快，结束的时候慢；
> 
> -  linear动画速度不变（默认）；



 

callback：组件动画结束回调函数，可选参数，入参为Json对象，定义如下：  

> code：回应状态码，数字【0,-1】  
> 
> -  0：执行动画成功；
> 
> - -1：执行动画失败； 


返回值：无  

示例：  

```javascript
var = {};
jsonData.type = "scale";
jsonData.duration = 300;

var settings = new Array(): Object;

var json = {};
json.value = 0.01;
json.keyTimes = 0;
json.curve = "linear";
settings.push(json);

json = {};
json.value = 1.1;
json.keyTimes = 0.5;
json.curve = "linear";
settings.push(json);

json = {};
json.value = 1.0;
json.keyTimes = 1.0;
json.curve = "ease_out";
settings.push(json);

jsonData.settings = settings;
thisDom.startKeyFrameAnimator(jsonData, aniCallBack);

```

**注：**   

- 帧动画本质上也是属性动画，其值修改后，组件真实属性也会变化，与属性动画不同的时，可以自己控制，在某个时间段上的动画效果的值。
 
- 帧动画执行后需要调用releaseAnimator()方法释放动画，效果和属性动画一样。

  
<span id="dhxg_4">**releaseAnimator(): void**</span>  

<code>结束控件动画</code>    

参数：无

返回值：无  

**注：** UI组件执行startAnimator() ，startKeyFrameAnimator()后，需要调用该方法告知系统动画已完成，组件自身才能被document.refresh()刷新方法刷新。  

 

<h2 id="cid_2">尺寸和位置</h2>

本节目录：  
> 
> [getFrame(): Object  获取组件在父容器中的位置](#cchwz_1)   
> 
> [setFrame(frame:Object):void  设置组件在父容器中的位置](#cchwz_2)   
> 
> [getCenter(): Object 获取组件中心点在父容器中的位置](#cchwz_3)  
>  
> [getAbsoluteFrame(): Object  获取组件在绘制窗口中的位置](#cchwz_4)   


<span id="cchwz_1">**getFrame(): Object**</span>  

<code>获取组件在父容器中的位置</code> 

参数：无  

返回值：json数据格式，定义如下：  

> x：float型，水平位置；  
> 
> y：float型，垂直位置；  
> 
> width：float型，宽度；  
> 
> height：float型，高度；

**注：** 该方法获取的是组件布局完毕后在父容器中的实际位置，与样式中的width和height是有区别的，比如style样式里面设置的是flex:1，该组件布局完成后就会有个实际的width、height、x和y值，但是样式是没有设置width和height样式属性的，所以只能通过v.getFrame().width来得到宽度，不能通过v.getStyle("width");得到宽度，如果没有定义width样式v.getStyle("width")会得到一个null值。  



<span id="cchwz_2">**setFrame(frame: Object): void**</span>  

<code>设置组件在父容器中的位置</code>  

参数：   

frame：json数据格式，定义如下：  

> x：float型，水平位置，必选项；
> 
> y：float型，垂直位置，必选项；
> 
> width：float型，宽度，必选项；
> 
> height：float型，高度，必选项；

返回值：无  

**注：**   

- 通过该方法设置frame， width，height设置至组件css样式中，x、y不会修改样式中的left和top属性。

- 设置frame后，如果执行了document.refresh()，x和y就会还原，如果不希望还原可以在通过setStyle()手动设置对应样式left和top。



<span id="cchwz_3">**getCenter(): Object**</span>  

<code>获取组件中心点在父容器中的位置</code>  

参数：无  

返回值：json数据格式，定义如下：  

> x：float型，水平位置；
>
> y：float型，垂直位置；


<span id="cchwz_4">**getAbsoluteFrame(): Object**</span>  


<code>获取组件在绘制窗口中的位置</code>

参数：无 

返回值：json数据格式，定义如下： 

> x：float型，水平位置；
> 
> y：float型，垂直位置；
> 
> width：float型，宽度；
> 
> height：float型，高度；

**注：**  

- 如果组件通过js动态加载进行布局，在android上可能不能马上获取到getAbsoluteFrame的值，需要做一个定时处理来获取。  

- 如果在页面加载的时候获取某一个组件的getAbsoluteFrame的值，在android上 在window的loaded事件里面可能获取不到，需要放在window的animator事件里面获取。



<h2 id="cid_3">普通Dom节点操作</h2>

本节目录：  
> 
> [getParent(): IElement 获取父节点](#ptdom_1)   
> 
> [getNext(): IElement 获取同级下一个节点](#ptdom_2)   
> 
> [getPrevious(): IElement 获取同级前一个节点](#ptdom_3)  
> 
> [remove(): void 从父容器中移除自身](#ptdom_4)  
> 
> [clone(isDeep:boolean): IElement 对当前Dom节点进行克隆](#ptdom_5)  
>  
> [setAttr(attrName:string,attrValue:string): void  设置节点属性](#ptdom_6)   
>
> [getAttr(attrName:string):string  获取节点属性](#ptdom_7) 
>
> [getAttrs(): Object 获取节点所有属性](#ptdom_8) 
>
> [removeAttr(attrName:string):void  移除节点属性](#ptdom_9)
>
> [hasAttr(attrName:string): boolean  节点是否具有该属性](#ptdom_10) 
>
> [setText(content:string):void  设置节点文本内容](#ptdom_11)
>
> [getText():void  获取节点文本内容](#ptdom_12)
> 
> [setStyle(styleName:string,styleValue:string): void  设置节点样式值](#ptdom_13)  
>
> [getStyle(styleName:string):string  获取节点样式值](#ptdom_14)   
>
> [clearStyle(styleName:string): void 移除节点样式值](#ptdom_15)   
>
> [setClassStyle(className:string,domobj:IElement): void  设置节点对应Class样式](#ptdom_16) 
>  
> [getClassStyle(): string 获取节点已设置Class样式](#ptdom_17)  
>  
> [getTag(): string 获取UI组件类型](#ptdom_18)  
>  
> [getId(): string 获取UI组件Id标识](#ptdom_19)  



<span id="ptdom_1">**getParent(): string**</span>  

<code>获取父节点</code>  

参数：无  

返回值：父节点dom对象  

示例： 

```javascript
var v = document.getElement("v_id");
var parentdom = v.getParent();
```  


<span id="ptdom_2">**getNext(): IElement**</span>  

<code>获取同级下一个节点</code> 

参数：无  

返回值：同级下一个节点 

示例：  

```javascript
var v = document.getElement("v_id");
var nextdom = v.getNext();
```  

<span id="ptdom_3">**getPrevious(): IElement**</span>  

<code>获取同级前一个节点</code>   

参数：无  

返回值：同级前一个节点  

示例：  

```javascript
var v = document.getElement("v_id");
var previousdom = v.getPrevious();
```  

<span id="ptdom_4">**remove(): void**</span>  

<code>从父容器中移除自身</code>  

参数：无  

返回值：无  

**注：**  该方法可以移除控件自身，不过控件对象并没有销毁，只是该控件的view被移除，比如移除后，可以继续使用appendChild(domObj:IElement): void这类方法，把该控件的view添加到其他容器中。  

示例： 

```javascript  
var v = document.getElement("v_id");
v.remove();
document.refresh();
```  

<span id="ptdom_5">**clone(isDeep:boolean): IElement**</span>  

<code>对当前Dom节点进行克隆</code>   

参数：  

isDeep：是否深度拷贝，可选项，【true,false】，若参数不存在等同于false  
> 
> true：克隆节点并递归地克隆子节点；
> 
> false：则只克隆该节点本身；  

**注：** id属性不支持拷贝  

示例： 

```javascript  
var v = document.getElement("v_id");
var clonedom  =  v.clone("true");
``` 

<span id="ptdom_6">**setAttr(attrName:string,attrValue:string): void**</span>  

<code>设置节点属性</code>  

参数：  

attrName：需设置节点属性名，字符串类型，必选项； 

attrValue：需设置节点属性值，字符串类型，必选项；

**注：** 这里设置节点的属性，不一定是组件本就具备的属性，也可以是自定义的属性名称和属性值。

示例： 

```javascript  
var v = document.getElement("v_id");
v.setAttr("value","123");
```   

<span id="ptdom_7">**getAttr(attrName:string):string**</span>  

<code>获取节点属性</code>  

参数：
attrName：需查询节点属性名，字符串，必选项类型；  

返回值：查询的节点属性值，字符串类型；  

示例： 

```javascript  
var v = document.getElement("v_id");
v.getAttr("value");
```   

<span id="ptdom_8">**getAttrs(): Object**</span>  

<code>获取节点所有属性</code>  

参数：无  

返回值：获取节点所有属性，Json类型；  

示例：

```javascript  
var v = document.getElement("v_id");
var attrs = v.getAttrs();

for (var ar in attrs) {
    if (ar != "style" && ar != "id" && ar != "class") {
       console.log(ar+":"+attrs[ar]);  
    }
}
```   

<span id="ptdom_9">**removeAttr(attrName:string): void**</span>  

<code>移除节点属性</code>  

参数： 

attrName：需移除节点属性名，字符串，必选项类型；  

返回值：无 

示例：

```javascript  
var v = document.getElement("v_id");
v.removeAttr("value");
```   

<span id="ptdom_10">**hasAttr(attrName:string): boolean**</span>  

<code>节点是否具有该属性</code>  

参数：  

attrName：需查询节点名，字符串，必选项类型；  

返回值：节点是否具有该属性，bool型  
 
> true：具有该属性；
> 
> false：不具有该属性；

```javascript  
var v = document.getElement("v_id");
var bl = v.hasAttr("value");
```   

<span id="ptdom_11">**setText(content:string): void**</span>  

<code>设置节点文本内容</code>  

参数：

content：需要设置文本内容，一般用于设施text组件的文本内容，字符串类型 

返回：无

示例：

```javascript  
var v = document.getElement("text_id");  
v.setText("123");  
```   



<span id="ptdom_12">**getText(): void**</span>  

<code>获取节点文本内容</code>  

参数：无 

返回值：当前节点文本内容，字符串类型

示例：

```javascript  
var v = document.getElement("text_id");  
var textstr = v.getText();  
```   


<span id="ptdom_13">**setStyle(styleName:string,styleValue:string): void**</span>  

<code>设置节点样式值</code>  

参数：  

styleName：需设置节点样式名，字符串类型，必选项；  

styleValue：需设置节点样式值，字符串类型，必选项；  

返回值：无  

**注：**  如果修改样式里面，包含有修改布局的样式，需要对布局进行刷新方可生效，一般影响布局的样式有width、height，flex等，如果只是修改颜色，不需要刷新。

示例：

```javascript  
var v = document.getElement("v_id");  
v.setStyle("background-color","red");  
```  


<span id="ptdom_14">**getStyle(styleName:string):string**</span>  

<code>获取节点样式值</code>  

参数： 

styleName：需查询节点样式名，字符串类型，必选项；  

返回值：查询的节点样式值，字符串类型；  

**注：**  如果通过组件style或class属性设置的color样式（如：#ff0000），在android上由于css引擎的差异性，通过getStyle("color")获取的颜色值是rgb(255,0,0)这种形式，通过js设置的颜色值则没有影响。

示例：

```javascript  
var v = document.getElement("v_id");  
v.getStyle("background-color");  
```  

<span id="ptdom_15">**clearStyle(styleName:string): void**</span>  

<code>移除节点样式值</code>  

参数：  

styleName：需设置节点样式名，字符串类型，必选项；  

返回值：无  

示例：

```javascript  
var v = document.getElement("v_id");  
v.clearStyle("background-color");  
```   

<span id="ptdom_16">**setClassStyle(className:string,domobj:IElement): void**</span>  

<code>设置节点对应Class样式</code>  

参数：  

className：需设置Class样式名，支持多个样式，以空格分隔，字符串类型，必选项；   


domObj：当前js运行环境对象，可选参数，component模板中使用，传入this即可；

返回值：无  

**注：**   

- 该法设置class后，以前的通过class设置的样式会全部清除，不过style设置的不会清除。
 
- 由于style的优先级要高于class，如果class设置的样式里面，包含之前style设置的样式，还是以style中的样式为优先，如果让class设置的样式值生效，可以清除style中相同的样式属性。


示例： 

```javascript  
//在uixml页面中
var v = document.getElement("v_id");  
v.setClassStyle("class1 class2");  
```   

```javascript  
//在模板页面中
var v = document.getElement("v_id");  
v.setClassStyle("class1 class2",this);  
```   


<span id="ptdom_17">**getClassStyle(): string**</span>  

<code>获取节点已设置Class样式</code>

参数：无 

返回值：已设置Class样式，字符串类型； 

示例： 

```javascript  
var v = document.getElement("v_id");  
var classstr =  v.getClassStyle();  
```   


<span id="ptdom_18">**getTag(): string**</span>  

<code>获取UI组件类型</code>   

参数：无  

返回值：UI组件类型，字符串类型，如button组件则返回"button",box组件则返回"box";  

示例：

```javascript  
var v = document.getElement("v_id");  
var domstr =  v.getTag();  
```  

<span id="ptdom_19">**getId(): string**</span>  

<code>获取UI组件Id标识</code>   

示例：

```javascript  
var v = document.getElement("v_id");  
var domid =  v.getId();  
```  

<h2 id="cid_4">容器类Dom节点操作</h2>

本节目录：  
> 
> [getElement (id:string): IElement 根据Id获取容器内UI控件对象](#rqczdom_1)   
> 
> [getElements(rule:string): Array&lt;Object&gt; 根据特定规则获取容器内UI控件对象集](#rqczdom_2)   
> 
> [getChildren():Array&lt;IElement&gt;  容器获取子节点集](#rqczdom_3)  
>  
> [getFirstChild(): IElement 容器获取首子节点](#rqczdom_4) 
>  
> [getLastChild(): IElement 容器获取尾节点](#rqczdom_5) 
>  
> [appendChild(domObj:IElement):void  容器添加子节点至尾部](#rqczdom_6)
>  
> [insertBefore(domObj:IElement,beforeDomObj:IElement): void 容器在指定的已有的子节点之前插入新节点](#rqczdom_7) 
>  
> [insertAfter (domObj:IElement,afterDomObj:IElement): void  容器在指定的已有的子节点之后插入新节点](#rqczdom_8) 
>  
> [replaceChild(newDomObj:IElement,oldDomObj:IElement): void  容器替换子节点](#rqczdom_9) 
>  
> [clear(): void 清空容器内所有子节点](#rqczdom_10) 
>  
> [getInnerHTML(): string 动态获取容器内子节点xml](#rqczdom_11)   




<span id="rqczdom_1">**getElement(id:string): IElement**</span>  

<code>根据Id获取容器内UI控件对象</code>   

参数：  

id：UI组件的唯一标识，字符串类型；

返回值：控件dom对象，若查找失败则返回null  

示例：

```javascript  
var box = document.getElement("box_id");  

//得到box内部某一个组件对象
var v =box.getElement("v_id");  

```  

<span id="rqczdom_2">**getElements(rule:string):Array&lt;IElement&gt;**</span>   

<code>根据特定规则获取容器内UI控件对象集</code>   

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
var box = document.getElement("box_id");  

//根据类型选择器， 得到box下级节点里面所有text组件对象数组
var v = boxgetElements("text");  

//根据ID选择器， 得到box下级节点里面所有id为ext_id对象数组
var v = box.getElements("#text_id");  

//类选择器， 得到box下级节点里面所有class类为text_class对象数组,，如：<text class="text_class">11</text>
var v = box.getElements("#text_class");  

//属性选择器， 得到box下级节点里面所有属性gourp="abc"对象数组,，如：<text gourp="abc">11</text>
var v = box.getElements('[gourp="abc"]');  

```    


<span id="rqczdom_3">**getChildren():Array<IElement>**</span>   

<code>容器获取子节点集</code>   

参数：无  

返回值：包含子节点dom对象数组，若无子节点则返回空数组  

示例：

```javascript  
var box = document.getElement("box_id");  
var arr = box.getChildren();  
```  

<span id="rqczdom_4">**getFirstChild(): IElement**</span>   

<code>容器获取首子节点</code>  

参数：无 

返回值：获取容器首节点，若不存则返回null  

示例：

```javascript  
var box = document.getElement("box_id");  
var v = box.getFirstChild();  
```  


<span id="rqczdom_5">**getLastChild(): IElement**</span>  

<code>容器获取尾节点</code>  

参数：无 

返回值：获取容器首节点，若不存则返回null 

示例：

```javascript  
var box = document.getElement("box_id");  
var v = box.getLastChild();  
```   



<span id="rqczdom_6">**appendChild(domObj:IElement): void**</span>   

<code>容器添加子节点至尾部</code>  

参数： 

domObj：需添加的子节点对象，必选项； 

返回值：无

**注：** 

- 执行该方法，需要刷新容器布局方可生效。

- 向某个容器添加节点的时候，如果该容器正在监听touch系列事件，会造成事件中断。

示例：

```javascript  
var box = document.getElement("box_id");  
var box1 = document.getElement("box1_id");  
box.appendChild(box1);  
```   



<span id="rqczdom_7">**insertBefore(domObj:IElement,beforeDomObj:IElement): void**</span>   

<code>容器在指定的已有的子节点之前插入新节点</code> 

参数：  

domObj：需添加Dom节点，必选项；  

beforeDomObj：  在其之前插入新节点的子节点，必选项；   

返回值：无  

**注：** 执行该方法，需要刷新容器布局方可生效。

示例：

```javascript  
var box = document.getElement("box_id");  
var box1 = document.getElement("box1_id");  
box.insertBefore(box1);  
```   


<span id="rqczdom_8">**insertAfter (domObj:IElement,afterDomObj:IElement): void**</span>   

<code>容器在指定的已有的子节点之后插入新节点</code>  

参数：  

domObj：需添加Dom节点，必选项；  

afterDomObj：在其之后插入新节点的子节点，必选项；   

返回值：无

**注：** 执行该方法，需要刷新容器布局方可生效。

示例：

```javascript  
var box = document.getElement("box_id");  
var box1 = document.getElement("box1_id");  
box.insertAfter(box1);  
```    


<span id="rqczdom_9">**replaceChild(newDomObj:IElement,oldDomObj:IElement): void**</span>  

<code>容器替换子节点</code>

参数：

newDomObj：新Dom节点，必选项；

oldDomObj：老Dom节点，必选项；

返回值：无  

**注：** 执行该方法，需要刷新容器布局方可生效。

示例：

```javascript  
var box = document.getElement("box_id");  
var box1 = document.getElement("box1_id");  
var box2 = document.getElement("box2_id"); 
box.replaceChild(box1,box2);  
```  


<span id="rqczdom_10">**clear(): void**</span>  

<code>清空容器内所有子节点</code>   

参数：无 

返回值：无 

**注：** 执行该方法，需要刷新容器布局方可生效。

示例：

```javascript  
var box = document.getElement("box_id");  
box.clear();  
```  

<span id="rqczdom_11">**getInnerHTML(): string**</span>

<code>动态获取容器内子节点xml</code>   

参数：无 

返回值：容器内子节点xml，字符串类型 

示例：
 
```javascript  
var box = document.getElement("box_id");  
var strxml =  box.getInnerHTML(); 
```  