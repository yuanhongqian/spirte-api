# gaodemap 组件使用 

----------

高德地图UI组件,提供高德地图功能集成，高德地图默认坐标系为gcj02。  

gaodemap为内置UI组件


<h2 id="cid_0">属性</h2> 

本节目录：

> [公共属性](#sx_0)	
> 
> [maptype	地图显示方式](#sx_1)
>
>[traffic	  是否显示交通图](#sx_2)
>
>[gesture  是否禁用所有手势](#sx_3)
>
>[zoom  是否启用缩放手势（可以通过js修改）](#sx_4)
>
>[zoomLevel  地图缩放比例](#sx_5)
>
>[scroll 	是否启用平移手势](#sx_6)
>
>[scaleControl  是否显示地图比例尺](#sx_12)
>
>[zoomControl  是否显示地图缩放按钮](#sx_13)


<span id="sx_0">**公共属性**</span>  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-api/ggsx.html)，包括：id、style、class；

<span id="sx_1">**maptype**</span>

<code>地图显示方式</code>

字符串枚举型,取值[normal, satellite]

> normal：普通地图（默认）
> 
> satellite：卫星地图


<span id="sx_2">**traffic**</span>

<code>是否显示交通图</code>

bool型

> true：显示交通图
> 
> false：不显示交通图(默认)

<span id="sx_3">**gesture**</span>

<code>是否禁用所有手势</code>

bool型

> true：开启地图所有手势事件 (默认)
> 
> false：禁用地图所有手势事件

<span id="sx_4">**zoom**</span>

<code>是否启用缩放手势</code>

bool型

> true：启用缩放手势(默认)
> 
> false：不启用缩放手势


<span id="sx_5">**zoomLevel**</span>

<code>地图缩放比例</code>

取值范围[3-20],默认15，float数字类型

<span id="sx_6">**scroll**</span>

<code>是否启用平移手势</code>

bool型

> true：启用平移手势(默认)
> 
> false：不启用平移手势


<span id="sx_12">**scaleControl**</span>

<code>是否显示地图比例尺</code>

bool型

> true：显示地图比例尺(默认)
> 
> false：不显示地图比例尺

<span id="sx_13">**zoomControl**</span>

<code>是否显示地图缩放按钮</code>

bool型

> true：显示地图缩放按钮(默认)
> 
> false：不显示地图缩放按钮

注：仅Android支持





<h2 id="cid_1">样式</h2>

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-api/ggys.html)，包括：  

> 尺寸
> 
> 定位 
> 
> 外边距
> 
> flexbox布局：align-self,flex




<h2 id="cid_2">事件</h2>

本节目录：

> **地图事件**
> 
> [click  单击地图空白区域触发](#sj_1)
> 
> [longClick  长按地图触发 ](#sj_4) 
> 
> [mapStatusChangeFinish   地图状态改变结束触发](#sj_5)
>
> [mapStatusChange 地图状态改变过程中国触发 ](#sj_10)
>
> **普通Mark点事件**  
> 
> [markClick  单击地图mark标注点触发](#sj_6)
> 
> [markDragStart  拖动mark标注点开始时触发](#sj_7)
> 
> [markDragEnd  拖动mark标注点结束时触发](#sj_8)
> 
> **定位点事件**
> 
> [locationChange  地图启动定位后，接收到系统定位数据改变时触发](#sj_9)

 
<span id="sj_1">**click**</span>

<code>单击地图空白区域触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：click；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
 
param对象为Json对象,定义如下：

> latitude：点击位置纬度,数字类型
> 
> longitude：点击位置经度,数字类型


<span id="sj_4">**longClick**</span>

<code>长按地图触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：longClick；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
    
param对象为Json对象,定义如下：

> latitude：长按位置纬度,数字类型,
> 
> longitude：长按位置经度,数字类型, 


<span id="sj_5">**mapStatusChangeFinish**</span>

<code>地图状态改变结束触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：mapStatusChangeFinish；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
    
param对象为Json对象,定义如下：

> latitude：地图中心点位置纬度,数字类型,
> 
> longitude：地图中心点位置经度,数字类型
> 
> zoom：地图当前缩放比例，数字类型


<span id="sj_10">**mapStatusChange**</span>

<code>地图状态改变过程中国触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：mapStatusChange；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
    
param对象为Json对象,定义如下：  

> latitude：地图中心点位置纬度,数字类型
> 
> longitude：地图中心点位置经度,数字类型
> 
> zoom：地图当前缩放比例，数字类型

**注：仅Android支持**


<span id="sj_6">**markClick**</span>

<code>单击地图mark标注点触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：markClick；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
    
param对象为Json对象,定义如下：

> id：标注点标识值,字符串类型 
> 
> latitude：纬度,数字类型
> 
> longitude：经度,数字类型；
>
> icon：标注点图标路径,字符串类型,本地图片：res:前缀,file:前缀
> 
> coorType：坐标系类型,字符串枚举型,[wgs84,gcj02]
> 
> - wgs84：标准gps坐标系
> 
> - gcj02：由中国国家测绘局制订的地理信息系统的坐标系统
> 
> title：标注点名称,字符串类型  
> 
> draggable：标注点是否可拖拽,bool型
> 
> -  true：可拖拽,
> 
> -  false：不可拖拽
> 
> rotate：标注点旋转角度,数字    
>    
> alpha：标注点透明度,数字,[0-1]
> 
> data：标注点传递附加参数，可选项，json类型

<span id="sj_7">**markDragStart**</span>

<code>拖动mark标注点开始时触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：markDragStart；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
    
param对象为Json对象,定义如下：

> id：标注点标识值,字符串类型 
> 
> latitude：纬度,数字类型
> 
> longitude：经度,数字类型；
> 
> icon：标注点图标路径,字符串类型,本地图片：res:前缀,file:前缀
> 
> coorType：坐标系类型,字符串枚举型,[wgs84,gcj02]
> 
> -   wgs84：标准gps坐标系
> 
> -   gcj02：由中国国家测绘局制订的地理信息系统的坐标系统
> 
> title：标注点名称,字符串类型  
> 
> draggable：标注点是否可拖拽,bool型
> 
> -  true：可拖拽
> 
> -  false：不可拖拽
> 
> rotate：标注点旋转角度,数字
> 
> alpha：标注点透明度,数字,[0-1]
> 
> data：标注点传递附加参数，可选项，json类型



<span id="sj_8">**markDragEnd**</span>

<code>拖动mark标注点结束时触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：markDragEnd；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
    
param对象为Json对象,定义如下：

> id：标注点标识值,字符串类型 
> 
> latitude：纬度,数字类型
> 
> longitude：经度,数字类型；
> 
> icon：标注点图标路径,字符串类型,本地图片：res:前缀,file:前缀
> 
> coorType：坐标系类型,字符串枚举型,[wgs84,gcj02]
> 
> - wgs84：标准gps坐标系
> 
> - gcj02：由中国国家测绘局制订的地理信息系统的坐标系统
> 
> title：标注点名称,字符串类型    
> 
> draggable：标注点是否可拖拽,bool型,true：可拖拽,false：不可拖拽
> 
>  rotate：标注点旋转角度,数字   
> 
> alpha：标注点透明度,数字,[0-1]
> 
> data：标注点传递附加参数，可选项，json类型


<span id="sj_9">**locationChange**</span>

<code>地图启动定位后，接收到系统定位数据改变时触发</code>

event事件对象包括：  

> type：事件类型,字符串类型,固定值：locationChange；
> 
> target：触发事件的目标组件,dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
    
param对象为Json对象,定义如下：

> latitude：定位点纬度,数字类型
> 
> longitude：定位点经度,数字类型
> 
> accuracy：定位精度，数字，单位：米
> 
> direction：方向，数字，0-360，未获取返回-1
> 
> speed：速度，数字，单位：m/s，定位类型为gps时可用，未获取返回-1
> 
> altitude：海拔高度，数字，单位：米，定位类型为gps时可用。



<h2 id="cid_3">js方法</h2>

本节目录：

> [公共方法](#ff_0)
> 
> **标注点**
> 
> [addMark(jsonData:Object,domObj:IElement):Object   添加单个Mark标注点](#ff_1)
> 
> [removeMark(jsonData:Object): boolean  移除单个Mark标注点  ](#ff_2)
> 
> [updateMark(jsonData:Object,domObj:IElement): boolean  更新单个Mark标注点](#ff_3)
> 
> [addMarks(arrayData:Array&lt;Object&gt;,arrayDomObj:Array&lt;IElement&gt;): Array&lt;Object&gt;   添加多个Mark标注点](#ff_4) 
> 
> [removeMarks(jarrayData:Array&lt;Object&gt;): void   移除多个Mark标注点](#ff_5)
> 
> [clearMarks(): boolean  移除地图上所有Mark标注点](#ff_6)
>
> [showMarkPop(jsonData:Object):void   弹出mark点指定的pop窗口 ](#ff_42)
>
> [hideMarkPop(jsonData:Object):void   隐藏mark点弹出的pop窗口](#ff_43)
> 
>[marksZoomToSpan(jarrayData:Array&lt;Object&gt;,animator:boolean):void    指定mark点集合缩放至屏幕可见区域](#ff_tospan)
>
> **定位**
> 
> [startLocation(jsonData:Object): void  启动定位并展示定位图层](#ff_7)
> 
> [stopLocation(): void  关闭定位并关闭定位图册 ](#ff_8) 
> 
> **覆盖物** 
> 
> [addLine(jsonData:Object): string  地图添加折线](#ff_10)
> 
> [addCircle(jsonData:Object): string  地图添加圆形覆盖物 ](#ff_11)
> 
> [addArc(jsonData:Object): string  地图添加弧线](#ff_12)
> 
> [addPolygon(jsonData:Object): string  地图添加多边形](#ff_13)
> 
> [addText(jsonData:Object): string  地图添加文字](#ff_14)
> 
> [removeOverlay(jsonData:Object): boolean  移除遮盖物](#ff_15)
> 
> [clearOverlays(): boolean  移除所有遮盖物](#ff_16)
> 
> **路线规划标注**
> 
> [markTransitRoute(jsonData:Object,callback:Function): void  公交路径规划并标注  ](#ff_17)
> 
> [markDrivingRoute(jsonData:Object,callback:Function): void  驾车路径规划并标注](#ff_18)
> 
> [markWalkingRoute(jsonData:Object,callback:Function): void   步行路径规划并标注](#ff_19)
> 
> [markBikingRoute(jsonData:Object,callback:Function): void  骑行路径规划并标注](#ff_20)
> 
> [removeRoute (jsonData:Object): void   移除地图中指定标注规划路线](#ff_21)
> 
>[ clearRoutes(): void  清除地图中所有标注规划路线](#ff_22)
> 
> **行政区域检索标注** 
> 
> [markDistrict (jsonData:Object,callback:Function): void   行政区域检索并标注](#ff_23)
> 
> [removeDistrict (jsonData:Object): void 移除地图中指定区域标注](#ff_24)
> 
> [clearDistricts(): void 清除地图中所有标注区域 ](#ff_25)
> 
> **公交路线查询标注** 
> 
> [markBusLine(jsonData:Object,callback:Function): void  公交路线查询并标注](#ff_26)
> 
> [removeBusLine(jsonData:Object): void  移除地图中指定标注公交路线](#ff_27)
> 
> [clearBusLines(): void  清除地图中所有标注公交路线 ](#ff_28)
> 
> **地图系统标识**
> 
> [setLogoPosition(position:string): void设置高德地图logo显示位置](#ff_33)
> 
> [setZoomControlsPosition(position:string): void设置缩放按钮显示位置](#ff_34)
> 
> **其他**
> 
> [setMapCenter(jsonData:Object): boolean  设置地图中心点位置](#ff_29) 
> 
> [getMapCenter(): Object  获取地图中心点位置](#ff_30)
> 
> [getBounds(): Object  返回地图可视区域,以地理坐标表示 ](#ff_31)
> 
> [snapshot(jsonData:Object,callback:Function): void   地图截屏](#ff_32)



<span id="#ff_0"><code>**公共方法**</code></span>

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
> [clone(isDeep:boolean):IElement  对当前Dom节点进行克隆](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_5)
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


<span id="ff_1">**addMark(jsonData:Object,domObj:IElement): string **</span>

<code>添加单个Mark标注点</code>

参数：

 jsonData：需添加标注点数据,Json对象,定义如下：

> latitude：纬度,数字类型,必选项；
> 
> longitude：经度,数字类型,必选项；
>  
> coorType：坐标系类型,字符串枚举型,可选项,[wgs84,gcj02]
> 
> - wgs84：标准gps坐标系
> 
> - gcj02：由中国国家测绘局制订的地理信息系统的坐标系统(默认)
> 
> icon：标注点图标路径，可选项，字符串类型，本地图片：res:前缀，file:前缀
> 
> icons：标注点图标集路径，字符串数组类型，可选项，数组成员定义为，本地图片：res:前缀，file:前缀。注：icon与icons不可同时使用
> 
> iconDuration：标注点图标集每张图片切换间隔时间，数字类型，单位毫秒；
> 
> iconWidth：标注点图标宽度，可选项，数字类型，单位dp
> 
> iconHeight：标注点图标高度，可选项，数字类型，单位dp
> 
> title：标注点名称,字符串类型,可选项
> 
> data：标注点传递附加参数，可选项，json类型
> 
> titleSize：标注点文字字体大小，数字类型，默认12
> 
> titleColor：标注点文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb），默认#000000
> 
> titleWidth：标注点文字绘制最大宽度，单位dp，数字类型，默认80
> 
> layoutType：标注点布局模式，字符串枚举型，【left，right，top，bottom】，left：图左字右，right：图右字左，top：图上字下，bottom：图下字上
> 
> anchorX：标注点图片中心点X轴偏移比例，取值范围【0,1】，默认0.5，即水平居中
> 
> anchorY：标注点图片中心点Y轴偏移比例，取值范围【0,1】，默认1，即垂直下对齐
>  
> draggable：标注点是否可拖拽,bool型,可选项,true：可拖拽,false：不可拖拽（默认）
> 
> rotate：标注点逆时针旋转角度,数字,取值范围0-360,可选项,默认为0不旋转。注：仅Android支持
> 
> alpha：标注点透明度,数字,[0-1],可选项,默认为1不透明,注：仅Android支持
> 

domObj：需要显示的UI组件dom对象，IElement类型，可选项；

返回值： 添加成功返回数据，json格式如下： 

> id: 添加成功标注点标识值,字符串类型


<span id="ff_2">**removeMark(jsonData:Object): boolean**</span>

<code>移除单个Mark标注点</code>

参数：

jsonData：需移除标注点数据,Json对象,定义如下：

> id：需移除标注点标识值,字符串类型,必选项； 

返回值：移除标注点是否成功

<span id="ff_3">**updateMark(jsonData:Object,domObj:IElement): boolean**</span>

<code>更新单个Mark标注点</code>

参数：

 jsonData：需更新标注点数据,Json对象,定义如下：

> id：需更新标注点标识值,字符串类型,必选项；
>  
> latitude：纬度,可选项,数字类型
> 
> longitude：经度,可选项,数字类型；
>  
> coorType：坐标系类型,字符串枚举型,可选项,[wgs84,gcj02]
> 
> - wgs84：标准gps坐标系
> 
> - gcj02：由中国国家测绘局制订的地理信息系统的坐标系统
> 
> icon：标注点图标路径,字符串类型,可选项,本地图片：res:前缀,file:前缀
> 
> title：标注点名称,字符串类型,可选项
>  
> data：标注点传递附加参数，可选项，json类型
>  
>icons：标注点图标集路径，字符串数组类型，可选项，数组成员定义为,本地图片：res:前缀,file:前缀，注：icon与icons不可同时使用
>
> iconDuration：标注点图标集每张图片切换间隔时间,数字类型,单位毫秒；
> 
> iconWidth：标注点图标宽度，可选项，数字类型，单位dp
> 
> iconHeight：标注点图标高度，可选项，数字类型，单位dp
> 
> titleSize：标注点文字字体大小，数字类型，默认12
> 
> titleColor：标注点文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb），默认#000000
> 
> titleWidth：标注点文字绘制最大宽度，单位dp，数字类型，默认80
> 
> layoutType：标注点布局模式，字符串枚举型，【left，right，top，bottom】，left：图左字右，right：图右字左，top：图上字下，bottom：图下字上
> 
> anchorX：标注点图片中心点X轴偏移比例，取值范围【0,1】，默认0.5，即水平居中
> 
> anchorY：标注点图片中心点Y轴偏移比例，取值范围【0,1】，默认1，即垂直下对齐

> draggable：标注点是否可拖拽,bool型,可选项,true：可拖拽,false：不可拖拽（默认）
>  
> rotate：标注点旋转角度,数字,可选项,默认为0不旋转。注：仅Android支持
> 
> alpha：标注点透明度,数字,[0-1],可选项,默认为1不透明,注：仅Android支持
>

domObj：需要显示的pop弹出框的UI组件dom对象，IElement类型，可选项；
 

返回值：更新标注点是否成功

<span id="ff_4">**addMarks(arrayData:Array&lt;Object&gt;,arrayDomObj:Array&lt;IElement&gt;): Array&lt;Object&gt; **</span>

<code>添加多个Mark标注点</code>

参数：

arrayData：需添加标注点集合数据,数组类型,数组成员为Json对象,定义如下：

> latitude：纬度,数字类型,必选项；
> 
> longitude：经度,数字类型,必选项；
> 
> coorType：坐标系类型,字符串枚举型,可选项,[wgs84,gcj02]
> 
> - wgs84：标准gps坐标系
> 
> - gcj02：由中国国家测绘局制订的地理信息系统的坐标系统（默认）
>  
> icon：标注点图标路径,必选项,字符串类型,本地图片：res:前缀,file:前缀
> 
>icons：标注点图标集路径，字符串数组类型，可选项，数组成员定义为,本地图片：res:前缀,file:前缀，注：icon与icons不可同时使用
>
> iconDuration：标注点图标集每张图片切换间隔时间,数字类型,单位毫秒；
> 
> iconWidth：标注点图标宽度，可选项，数字类型，单位dp
> 
> iconHeight：标注点图标高度，可选项，数字类型，单位dp
>  
> title：标注点名称,字符串类型,可选项
> 
> data：标注点传递附加参数，可选项，json类型
>
> titleSize：标注点文字字体大小，数字类型，默认12
> 
> titleColor：标注点文字色值，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb），默认#000000
> 
> titleWidth：标注点文字绘制最大宽度，单位dp，数字类型，默认80
> 
> layoutType：标注点布局模式，字符串枚举型，【left，right，top，bottom】，left：图左字右，right：图右字左，top：图上字下，bottom：图下字上
> 
> anchorX：标注点图片中心点X轴偏移比例，取值范围【0,1】，默认0.5，即水平居中
> 
> anchorY：标注点图片中心点Y轴偏移比例，取值范围【0,1】，默认1，即垂直下对齐
> 
> draggable：标注点是否可拖拽,bool型,可选项,true：可拖拽,false：不可拖拽（默认）
>  
> rotate：标注点旋转角度,数字,可选项,默认为0不旋转。注：仅Android支持。
> 
> alpha：标注点透明度,数字,【0-1】,可选项,默认为1不透明,注：仅Android支持
> 

arrayDomObj：需要显示的UI组件数组，与arrayData一一对应，数组成员为dom对象，IElement类型，可选项；


返回值：添加成功标注点集合，数组类型,数组成员为Json对象,定义如下：  

> id：添加成功标注点标识值,字符串类型



<span id="ff_5">**removeMarks(jarrayData:Array&lt;Object&gt;): void**</span>

<code>移除多个Mark标注点</code>

参数：

arrayData：需移除标注点集合,数组类型,数组成员为Json对象,定义如下：

> id：需移除标注点标识值,字符串类型,必选项； 

返回值：无 


<span id="ff_6">**clearMarks(): boolean**</span>

<code>移除地图上所有Mark标注点</code>

参数：无

返回值：是否移除成功


<span id="ff_42">**showMarkPop(jsonData:Object):void **</span>

<code> 弹出mark点指定的pop窗口</code>

参数： 

jsonData：弹出mark点pop窗口入参，json格式，定义如下： 
> 
> id：标注点标识值,字符串类型，必选项

返回值：无 


<span id="ff_43">**hideMarkPop(jsonData:Object):void    **</span>

<code> 隐藏mark点弹出的pop窗口</code>

参数：

jsonData：隐藏mark点pop窗口入参，json格式，定义如下：
> 
> id：标注点标识值,字符串类型，必选项

返回值：无


<span id="ff_tospan">**marksZoomToSpan(jarrayData:Array&lt;Object&gt;,animator:boolean):void **</span>

<code> 指定mark点集合缩放至屏幕可见区域</code>

参数：

jarrayData：标准点集合，数组类型，数组成员json对象，定义如下：

> id: 标注点标识值，字符串类型，必选项；

animator：是否使用动画，boolean型，true:使用，false:不使用

返回值：无

<span id="#ff_7">**startLocation(jsonData:Object):void**</span>

<code>启动定位并展示定位图层</code>

参数：

jsonData：定位点参数配置，json对象，定义如下：

> accuracyCircleFillColor：精度圈填充颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）,(#aarrggbb)可选项
> 
> accuracyCircleStrokeColor：精度圈边框颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,十六进制（#rrggbb）,（#aarrggbb）可选项
> 
> icon：定位点图标路径，字符串类型，可选项，本地图片：res:前缀，file:前缀，注：仅Android支持
> 
> locationMode：定位图层显示方式，字符串枚举型，【normal，following，compass】
> - normal：普通模式（默认）；
> - following：跟随模式，箭头方向旋转，地图不变；
> - compass：罗盘模式，箭头方向及地图均旋转
> 
> locationButtonEnabled：系统定位按钮是否显示，bool型，true：显示；false：不显示；可选项，默认true。仅Android支持

返回值：无

<span id="#ff_8">**stopLocation():void**</span>

<code>关闭定位并关闭定位图层</code>

参数：无

返回值：无



<span id="ff_10">**addLine(jsonData:Object): string **</span>

<code> 地图添加折线</code>


参数：

jsonData：需要添加先参数,Json对象,定义如下：

> points：折线多个点组成的数组,数组成员为json对象,定义如下：
> - latitude：点纬度，数字类型，gcj02高德地图坐标系，必选项；
> - longitude：点经度，数字类型，gcj02高德地图坐标系，必选项；
> 
> lineColors：折线颜色组成的数组，数组成员为json对象，定义如下：
> - lineColor：线颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,rgba(255,0,0,0.5),十六进制（#rrggbb）,(#aarrggbb)可选项，默认黑色
> 
> lineWidth：线宽度，数字类型，2
> 
返回值：添加覆盖物唯一标识id值

<span id="#ff_11">**addCircle(jsonData:Object):string**</span>

<code>地图添加圆形覆盖物</code>

参数：

jsonData：需要添加圆形覆盖物参数，json类型，定义如下：

> latitude：圆中心点纬度，数字类型，gcj02高德地图坐标系，必选项。
> 
> longitude：圆中心点经度，数字类型，gcj02高德地图坐标系，必选项
> 
> radius：圆半径，数字类型，必选项
> 
> lineWidth：圆边框宽度，数字类型，默认2
> 
> lineColor：圆边框色，字符串类型，支持RGB（rgb(255, 0, 0)）,RGBA（rgba(255, 0, 0, 0.5)）,十六进制（#rrggbb）,（#aarrggbb）可选项,默认黑色
> 
> fillColor：圆中心填充色，字符串类型，支持RGB（rgb(255, 0, 0)），RGBA（rgba(255, 0, 0, 0.5)）,十六进制（#rrggbb）,（#aarrggbb）可选项,默认透明色

返回值：添加覆盖物唯一标识id值

<span id="#ff_12">addArc(jsonData:Object):string</span>

<code>地图添加弧线</code>

参数：

jsonData：需要添加线参数，json类型，定义如下：

> points：弧线多个点组成的数组，数组成员为json对象，定义如下：
> - latitude：点纬度，数字类型，gcj02高德地图坐标系，必选项；
> - longitude：点经度，数字类型，gcj02高德地图坐标系，必选项；
> 
> lineColor：弧线颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,rgba(255, 0, 0, 0.5),十六进制（#rrggbb）,（#aarrggbb）可选项,默认黑色
> 
> lineWidth：弧线宽度，数字类型，默认2

返回值：添加覆盖物唯一标识id值

注：仅Android支持

<span id="#ff_13">addPolygon(jsonData:Object):string</span>

<code>地图添加多边形</code>

参数：

jsonData：需要添加多边形参数，json类型，定义如下：

> points：多边形多个点组成的数组，数组成员为json对象，定义如下：
> - latitude：点纬度，数字类型，gcj02高德地图坐标系，必选项；
> - longitude：点经度，数字类型，gcj02高德地图坐标系，必选项；
> 
> lineColor：边框线颜色，字符串类型，支持RGB（rgb(255, 0, 0)）,rgba(255, 0, 0, 0.5),十六进制（#rrggbb）,（#aarrggbb）可选项,默认黑色
> 
> lineWidth：边框线宽度，数字类型，默认2
> 
> fillColor：圆中心填充色，字符串类型，支持RGB（rgb(255, 0, 0)），RGBA（rgba(255, 0, 0, 0.5)）,十六进制（#rrggbb）,（#aarrggbb）可选项,默认透明色

返回值：添加覆盖物唯一标识id值


<span id="ff_14">**addText(jsonData:Object): string**</span>

<code>地图添加文字</code>

**注：**仅Android支持

参数：

jsonData：需要添加文字参数,json类型,定义如下：

> latitude：文字纬度,数字类型,gcj02高德地图坐标系,必选项
> 
> longitude：文字经度,数字类型，gcj02高德地图地图坐标系,必选项
> 
> text：文字值,字符串类型,必选项
> 
> color：文字颜色,字符串类型,支持RGB（rgb(255, 0, 0)）,rgba(255, 0, 0, 0.5),十六进制（#rrggbb）,（#aarrggbb）可选项,默认黑色
> 
> size：文字尺寸,数字类型,可选项,默认15
> 
> bgColor：文字背景色,字符串类型,支持RGB（rgb(255, 0, 0)）,RGBA（rgb(255, 0, 0,0.5)）,十六进制（#rrggbb）,（#aarrggbb）可选项,默认透明色
> 
> rotate：文字旋转角度,逆时针,数字类型,可选项

返回值：添加覆盖物唯一标识id值



<span id="ff_15">**removeOverlay(jsonData:Object): boolean**</span>

<code>移除遮盖物</code>

参数：

jsonData：需移除遮盖物数据,Json对象,定义如下：

> id：需移除遮盖物标识值,字符串类型,必选项； 

返回值：移除遮盖物是否成功


<span id="ff_16">**clearOverlays(): boolean**</span>

<code>移除所有遮盖物</code>

参数：无

返回值：移除遮盖物是否成功


<span id="ff_17">**markTransitRoute(jsonData:Object,callback:Function): void**</span>

<code>公交路径规划并标注</code>

参数：

jsonData：公交路线标注参数,Json对象定义如下：

> fromLatitude：起点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> fromLongitude：起点经度，数字类型，gcj02高德地图坐标系，可选项；
> 
> toLatitude：终点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> toLongitude：终点经度，数字类型，gcj02高德地图坐标系，可选项
> 
> city：需查询的公交路线所在城市名,字符串类型,必选项
> 
> policy：公交查询策略,字符串枚举型,可选项,【BUS_COMFORTABLE,BUS_DEFAULT,BUS_LEASE_CHANGE,BUS_LEASE_WALK,BUS_NO_SUBWAY,BUS_SAVE_MONEY】

> - BUS_COMFORTABLE：最舒适;
> 
> - BUS_DEFAULT：最快捷模式（默认）
> 
> - BUS_LEASE_CHANGE：最少换乘；
> 
> - BUS_LEASE_WALK：最少步行；
> 
> - BUS_NO_SUBWAY：不乘地铁；
> 
> - BUS_SAVE_MONEY：最经济模式；
> 
> nightFlag：是否计算夜班车，数字枚举型，【0，1】，0：不计算（默认），1：计算

callFunction：结果回调,该回调函数具有Json对象入参,定义如下：

> code ：回应状态码,数字[0,-1]
> 
> -  0：标注成功；
> 
> -  -1：标注失败；
> 
> id：公交路线规划唯一标识,字符串类型；

返回值：无

<span id="ff_18">**markDrivingRoute(jsonData:Object,callback:Function): void**</span>

<code>驾车路径规划并标注</code>

参数：

jsonData：驾车路线标注参数,Json对象定义如下：

> fromLatitude：起点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> fromLongitude：起点经度,数字类型，gcj02高德地图坐标系，,可选项
> 
> toLatitude：终点纬度，数字类型,gcj02高德地图坐标系,可选项
> 
> toLongitude：终点经度,数字类型,gcj02高德地图坐标系，可选项
> 
> passByList：途经点参数,数组类型,可选参数,数组成员为Json对象,定义如下：
> 
> - passLatitude：途经点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> - passLongitude：途经点经度，数字类型,gcj02高德地图坐标系,可选项
> 
> avoidRoad：避让道路名称，可选项，字符串类型
> 
> policy：驾车查询策略字符串枚举型【DRIVING_SINGLE_AVOID_CONGESTION，DRIVING_SINGLE_DEFAULT，DRIVING_SINGLE_NO_EXPRESSWAYS，DRIVING_SINGLE_NO_HIGHWAY，DRIVING_SINGLE_NO_HIGHWAY_SAVE_MONEY，DRIVING_SINGLE_NO_HIGHWAY_SAVE_MONEY_AVOID_CONGESTION，DRIVING_SINGLE_SAVE_MONEY，DRIVING_SINGLE_SAVE_MONEY_AVOID_CONGESTION，DRIVING_SINGLE_SHORTEST】
> 
> - DRIVING_SINGLE_AVOID_CONGESTION：避免拥堵
> 
> - DRIVING_SINGLE_DEFAULT：速度优先（默认）
>
> - DRIVING_SINGLE_NO_EXPRESSWAYS：不走快速路。
>
> - DRIVING_SINGLE_NO_HIGHWAY：不走高速
> 
> - DRIVING_SINGLE_NO_HIGHWAY_SAVE_MONEY：不走高速且避免收费
> 
> - DRIVING_SINGLE_NO_HIGHWAY_SAVE_MONEY_AVOID_CONGESTION：不走高速且躲避收费和拥堵
> 
> - DRIVING_SINGLE_SAVE_MONEY：费用优先（不走收费路的最快道路）
> 
> - DRIVING_SINGLE_SAVE_MONEY_AVOID_CONGESTION：避免收费与拥堵
> 
> - DRIVING_SINGLE_SHORTEST：距离优先。


callFunction：结果回调,该回调函数具有Json对象入参,定义如下：

> code ：回应状态码,数字[0,-1]
> 
> - 0：标注成功；
> 
> - -1：标注失败；
> 
> id：驾车路线规划唯一标识,字符串类型；

返回值：无


<span id="ff_19">**markWalkingRoute(jsonData:Object,callback:Function): void**</span>

<code>步行路径规划并标注</code>

参数：
jsonData：路线标注参数,Json对象定义如下：

> fromLatitude：起点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> fromLongitude：起点经度，数字类型,gcj02高德地图坐标系，可选项
> 
> toLatitude：终点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> toLongitude：终点经度,数字类型,gcj02高德地图坐标系，可选项

callFunction：结果回调,该回调函数具有Json对象入参,定义如下：

> code ：回应状态码,数字[0,-1]
> 
> - 0：标注成功；
> 
> - -1：标注失败；
> 
> id：步行路线规划唯一标识,字符串类型；

返回值：无

**注：**步行规划目前仅支持同城


<span id="ff_20">**markBikingRoute(jsonData:Object,callback:Function): void**</span>

<code>骑行路径规划并标注</code>

参数：

jsonData：路线标注参数,Json对象定义如下：

> fromLatitude：起点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> fromLongitude：起点经度,数字类型,gcj02高德地图坐标系，可选项
> 
> toLatitude：终点纬度,数字类型,gcj02高德地图坐标系，可选项
> 
> toLongitude：终点经度,数字类型,gcj02高德地图坐标系，可选项

callFunction：结果回调,该回调函数具有Json对象入参,定义如下：

> code ：回应状态码,数字[0,-1]
> 
> - 0：标注成功；
> 
> - -1：标注失败；
> 
> id：骑行路线规划唯一标识,字符串类型；

返回值：无

**注：**骑行规划目前仅支持同城


<span id="ff_21">**removeRoute (jsonData:Object): void**</span>

<code>移除地图中指定标注规划路线</code>

参数：

jsonData：需移除规划路线参数,Json对象,定义如下：

> id：需移除规划路线标识值,字符串类型,必选项； 

返回值：无


<span id="ff_22">**clearRoutes(): void **</span>

<code>清除地图中所有标注规划路线</code>

参数：无 

返回值：无



<span id="ff_23">**markDistrict (jsonData:Object,callback:Function): void**</span>

<code>行政区域检索并标注</code>

参数：

jsonData：区域参数,Json对象定义如下：

> keywords：查询区域关键字,字符串类型,必选项
> 
> lineColor：边框线颜色,字符串类型,支持RGB（rgb(255, 0, 0)）,rgba(255, 0, 0, 0.5),十六进制（#rrggbb）,（#aarrggbb）可选项,默认#AA00FF88
> 
> lineWidth：边框线宽度,数字类型,默认2
> 
> fillColor：填充色,,字符串类型,支持RGB（rgb(255, 0, 0)）,RGBA（rgb(255, 0, 0)）,十六进制（#rrggbb）,（#aarrggbb）可选项,默认#AAFFFF00

callFunction：结果回调,该回调函数具有Json对象入参,定义如下：

> code ：回应状态码,数字[0,-1]
> 
> - 0：标注成功；
> 
> - -1：标注失败；
> 
> id：区域规划唯一标识,字符串类型；

返回值：无


<span id="ff_24">**removeDistrict (jsonData:Object): void**</span>

<code>移除地图中指定区域标注</code>

参数：

jsonData：需移除区域标注参数,Json对象,定义如下：

> id：需移除区域标注标识值,字符串类型,必选项； 

返回值：无



<span id="ff_25">**clearDistricts(): void**</span>

<code>清除地图中所有标注区域</code>

参数：无 

返回值：无


<span id="ff_26">**markBusLine(jsonData:Object,callback:Function): void**</span>

<code>公交路线查询并标注</code>

参数：

jsonData：公交路线标注参数,Json对象定义如下：

> busLine：需查询公交线路名称,字符串类型,必选项，关键字规则：多个关键字用“|”分割，“空格”表示与，“双引号”表示不可分割
> 
> city：需查询的公交所在城市名,字符串类型,必选项
    
callFunction：结果回调,该回调函数具有Json对象入参,定义如下：

> code ：回应状态码,数字[0,-1]
> 
> - 0：标注成功；
> 
> - -1：标注失败；
> 
> id：公交路线唯一标识,字符串类型；

返回值：无

**注:** 点击公交节点图标,弹出公交站点信息


<span id="ff_27">**removeBusLine(jsonData:Object): void**</span>

<code>移除地图中指定标注公交路线</code>

参数：

jsonData：需移除公交路线参数,Json对象,定义如下：

> id：需移除公交路线标识值,字符串类型,必选项； 

返回值：无

<span id="ff_28">**clearBusLines(): void**</span>

<code>清除地图中所有标注公交路线</code>

参数：无 

返回值：无

<span id="ff_33">**setLogoPosition(position:string): void**</span>

<code>设置高德地图logo显示位置</code>

参数：

position：高德地图logo位置，必选项字符串枚举型，【leftBottom，centerBottom，rightBottom】

返回值：无

**注：**高德地图logo默认显示于左下角

<span id="ff_34">setZoomControlsPosition(position:string):void</span>

<code>设置缩放按钮显示位置</code>

参数：

position：缩放按钮位置，必选项字符串枚举型，【rightCenter，rightBottom】

返回值：无

**注：**缩放按钮默认显示于右下角，仅Android支持


<span id="ff_29">**setMapCenter(jsonData:Object): boolean**</span>

<code>设置地图中心点位置</code>

参数：

jsonData：中心点设置,Json对象,定义如下：

> latitude：中心点纬度,数字类型,必选项；
> 
> longitude：中心点经度,数字类型,必选项；
> 
> coorType：坐标系类型,字符串枚举型,[wgs84,gcj02]
> 
> -   wgs84：标准gps坐标系
> 
> -   gcj02：由中国国家测绘局制订的地理信息系统的坐标系统（默认）
> 
> animator：地图移动是否使用动画，可选项，boolean型，true：使用动画；false：不使用动画（默认）

返回值：bool型,中心点是否设置成功

<span id="ff_30">**getMapCenter(): Object**</span>

<code>获取地图中心点位置</code>

参数：无

返回值：Json对象,定义如下：

> latitude：中心点纬度,数字类型；
> 
> longitude：中心点经度,数字类型；

**注：** 返回坐标系类型为gcj02坐标系



<span id="ff_31">**getBounds(): Object**</span>

<code>返回地图可视区域,以地理坐标表示</code>

参数：无

返回值：Json数据,定义如下：

> northeastLongitude：地图可视东北角的高德坐标系经度,gcj02高德地图坐标系,字符串；
> 
> northeastLatitude：地图可视东北角的高德坐标系纬度,gcj02高德地图坐标系,字符串；
> 
> southwestLongitude：地图可视区域西南角的高德坐标系经度,gcj02高德地图坐标系,字符串；
> 
> southwestLatitude：地图可视区域西南角的高德坐标系纬度,gcj02高德地图坐标系,字符串

**注：**返回坐标系类型为gcj02高德地图坐标系

<span id="ff_32">**snapshot(jsonData:Object,callback:Function): void**</span>

<code>地图截屏</code>

地图截屏,图片格式png

参数：
jsonData：截屏参数,Json对象,定义如下：

> path：截屏保存图片文件路径（包含文件名）,支持res: file:,字符串类型,必选项； 

callFunction：截屏回调,该回调函数具有Json对象入参,定义如下：

> code ：回应状态码,数字[0,-1]
> 
>  - 0：截屏成功；
>  
>  - -1：截屏失败；
> 
> path：生成截屏图片文件全路径,字符串类型；

返回值：无


<h2 id="cid_4">示例</h2>  

无
 


