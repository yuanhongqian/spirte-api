# imageshow 组件使用 

----------

imageshow图片预览组件支持浏览多张本地或网络图片，支持手势缩放原图，多图片支持左右滑动预览等，支持与其他UI组件配合构建自定义图片集展现，图片预览组件需指定宽高。

imageshow为内置UI组件

该控件只提供了一个可以缩放的图层，开发者可以结合其他控件进行组合，实现需要的效果。比如实现 新闻图片集查看的效果。



<h2 id="cid_1">属性</h2>   


**公共属性**  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-api/ggsx.html)，包括：id、style、class；  


**defaultSrc**  

<code>默认加载图片</code>    

网络加载过程中或图片加载失败时显示,只支持本地图片
本地图片：res:前缀,file:前缀,相对路径



<h2 id="cid_2">样式</h2>  

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-api/ggys.html)，包括：  
 
> 尺寸
> 
> 定位 
>  
> 背景
> 
> flexbox布局：align-self，flex

**cacheType**
	
<code>网络图片缓存方式</code>

网络图片缓存方式,[none,memory,disk] 

> none：不缓存
> 
> memory：程序启动后重新请求并缓存；
> 
> disk：缓存图片保留,下次程序启动读取缓存图片展现



<h2 id="cid_3">事件</h2>


	,


**click**  

<code>点击图片时触发</code>  

该事件会多次触发

event事件对象包括：  
> 
> type：事件类型,字符串类型,固定值：click；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型；

param对象为Json对象,定义如下：

> index：当前图片索引,数字类型；
> 
> src：当前图片路径,字符串类型；


**longTouch**  
 
<code>长按图片时触发</code> 

event事件对象包括：  

> type：事件类型,字符串类型,固定值：longTouch；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型；

param对象为Json对象,定义如下：

> index：当前图片索引,数字类型；
> 
> src：当前图片路径,字符串类型；


**pageSelected**  

<code>图片切换完成后触发</code> 

event事件对象包括：  

> type：事件类型,字符串类型,固定值：pageSelected；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
 
param对象为Json对象,定义如下：

> index：当前图片索引,数字类型；
> 
> src：当前图片路径,字符串类型；
> 

<h2 id="cid_4">js方法</h2>   


<span id="ff_1">**公共方法**</span>  

[事件相关](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_0)，包括：

> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Function&gt;  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_4)   

[动画相关](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_1)，包括： 
 
> [startAnimation(jsonData:Object,callback:Function): void  启动UI组件动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_1)   
> 
> [startAnimator(jsonData:Object,callback:Function): void  启动UI组件属性动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_2)   
> 
> [startKeyFrameAnimator(jsonData:Object,callback:Function): void  启动UI组件关键帧动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_3)  
>  
> [ releaseAnimator(): void  结束控件动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_4)   

[尺寸和位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_2)，包括：  

> [getFrame(): Object  获取组件在父容器中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_1)   
> 
> [setFrame(frame:Object): void  设置组件在父容器中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_2)   
> 
> [getCenter(): Object  获取组件中心点在父容器中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_3)  
>
> [getAbsoluteFrame(): Object  获取组件在绘制窗口中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_4)   


[普通Dom节点操作](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_3)，包括：  

> [getParent(): IElement  获取父节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_1)   
> 
> [getNext(): IElement  获取同级下一个节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_2)   
> 
> [getPrevious(): IElement  获取同级前一个节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_3)  
> 
> [remove(): void  从父容器中移除自身](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_4)  
> 
 
> [setAttr(attrName:string,attrValue:string): void  设置节点属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_6)   
>
> [getAttr(attrName:string):string  获取节点属性值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_7) 
>
> [getAttrs(): Object  获取节点所有属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_8) 
>
> [removeAttr(attrName:string): void  移除节点属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_9) 
>
> [hasAttr(attrName:string): boolean  节点是否具有该属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_10) 
> 
> [setStyle(styleName:string,styleValue:string): void  设置节点样式值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_13)  
>
> [getStyle(styleName:string):string  获取节点样式值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_14)   
>
> [clearStyle(styleName:string): void  移除节点样式值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_15)    
>
> [setClassStyle(className:string,domobj:IElement): void   设置节点对应Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.htm#ptdom_16) 
>  
> [getClassStyle(): string  获取节点已设置Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_17)  
>  
> [getTag(): string  获取UI组件类型](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_18)  
>  
> [getId(): string  获取UI组件Id标识](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_19) 



**addData(jsonData:Object): void**  

<code>添加图片集数据</code>

参数：

jsonData：添加图片集参数,Json对象,定义如下：

> index：传入页码索引,数字类型,默认从0开始计数,【0,num-1】可选项；
> 
> data：需要传递的图片集参数,数组类型,数组成员为Json对象定义如下：
> 
>- src：需要加载图片路径,字符串类型,必选项,支持本地图片（res：前缀）,网络图片（http://前缀）




