# 公共事件

----------
  
在Sprite平台中，所有事件均具备向上冒泡机制，所以我们有时候可以利用改机制监听最外层容器，然后通过even对象的target来判断内部是那个组件触发了该事件。

**click事件**  

<code>单击UI组件时候触发 </code>

event事件对象包括：  

>   type：事件类型，字符串类型，固定值：click；
>   
>   target：触发事件的目标组件，dom对象；
>   
>   timestamp：事件触发的时间戳,单位毫秒，数字类型

示例：   

```javascript
button.on("click",function(event){
    var eventType = event.type;
    var targetObj = event.target;
    var timestamp = event.timestamp;
});

```

**注：**  当某个控件同时有click和touchMove事件时，当touchMove事件触发后，click事件就会失效，这个特点可以用来做那种点上去如果反悔了可以移动手指让点击事件失效的效果。


**longTouch事件** 

<code> 长按UI组件时候触发 </code>

event事件对象包括：  

>   type：事件类型，字符串类型，固定值：longTouch；  
>     
>  target：触发事件的目标组件，dom对象；  
>     
>  timestamp：事件触发的时间戳,单位毫秒，数字类型
 

示例：  

```javascript
button.on("longTouch",function(event){
    var eventType = event.type;
    var targetObj = event.target;
    var timestamp = event.timestamp;
});

```

**注：**  如果触发了longTouch事件，click事件会失效。


 


