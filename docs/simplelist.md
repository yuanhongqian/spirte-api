# simplelist组件使用 

----------

simplelist简单列表布局组件，用于展现大量重复列表类数据，simplelist列表布局组件包括：header，cell，footer，refresh，left，right几个子容器，支持多cell模板，支持列表左右滑动，组合使用于不同场景下。

simplelist使用了模板机制及数据绑定来实现业务数据与列表UI组件的关联，通过SimpleListAdapter实现数据与简单列表的绑定，数据变化后调用SimpleListAdapter.refresh()刷新即可。

simplelist主要用于新闻展示类列表场景，开发者可根据场景需要选择使用list或simplelist。


<h2 id="cid_0">子节点</h2>

<code>header</code>

放置列表中固定于顶部显示的界面，采用flexbox模型不就，支持嵌套任意类型的或容器，使用和box容器一致。

通过simplelist对象getHeader()方法获取header对象后，可进行header容器内UI

<code>cell</cell>

用于放置列表item模板布局文件，采用flexbox模型布局，支持嵌套任意类型的UI组件或容器，使用和box容器一致。

某些复杂列表页面需要可能具有多个模板，支持放置多个cell容器用于区分，此时cell需要设置不同id属性用于区分。

<code>footer</code>

放置列表中固定于底部显示的界面，采用flexbox模型布局，支持嵌套任意类型的UI组件或容器，使用和box容器一致。

通过simplelist对象getFooter()方法获取footer对象后，可进行footer容器内UI组件相关操作，操作完毕后调用simplelist对象的refreshFooter方法刷新。

<code>refresh</code>

scroll处于垂直滚动模式时，可以包裹refresh容器用于实现下拉刷新及上拉刷新效果，详见[refresh](https://gitdocument.exmobi.cn/sprite-api/refresh.html)容器章节

<code>left</code>

用于放置列表左侧划出区域布局文件，采用flexbox模型布局，支持嵌套任意类型的UI组件或容器，使用和box容器一致。

simplelist列表中left最外层区域高度与item高度保持一致。

<code>right</code>

用于放置右侧划出区域布局文件，采用flexbox模型布局，支持嵌套任意类型的UI组件或容器，使用和box容器一致。

simplelist列表中right最外层区域高度与item高度保持一致。


<h2 id="cid_0">属性</h2> 

本节目录：  

> [公共属性](#sx_1)
> 
>[ scrollToTop  点击系统状态栏是否滚动至顶部](#sx_2)
> 
>[ bottomDistance  拖动至底部的距离](#sx_3)
>  
> [type  列表模式](#sx_4)
> 
> [slideState 列表滑动模式下状态设置](#sx_5)  



<span id="sx_1">**公共属性**</span>  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-api/ggsx.html)，包括：id、style、class；



<span id="sx_2">**scrollToTop**</span>    

<code>点击系统状态栏是否滚动至顶部</code>  

点击系统状态栏是否滚动至顶部，【true，false】
>true：点击系统状态栏滚动至顶部（默认）；
>false：点击系统状态栏不滚动至顶部；

**注：**仅iOS支持


<span id="sx_3">**bottomDistance**</span>  

<code>拖动至底部的距离</code>    

设置scrollToBottom触发事件后，拖动至底部多少距离时触发，数字，单位dp，默认为0
 


<span id="sx_4">**type**</span>  

<code>列表模式</code>   

列表模式，字符串枚举型，可选项【normal，slide】
> normal：普通列表（默认） 
> slide：左右滑动列表； 

<span id="#sx_5">**slideState**</span>

<code>列表滑动模式下状态设置</code>

列表滑动模式下状态设置，可选项【0，1】
> 0: 禁止滑动；
> 1：允许滑动

注：该属性可用于动态设置列表滑动模式下状态

<h2 id="cid_1">样式</h2>

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-api/ggys.html)，包括：  
 
> 尺寸
> 
> 定位 
> 
> 外边距
> 
> 背景
>
> flexbox布局：align-self，flex

<h2>事件</h2>

**scrollToBottom**

滚动条滚动至底部时触发，event事件对象包括：

> type：事件类型，字符串类型，固定值：scrollToBottom
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型

注：该触发事件一般与bottomDistance属性配合使用

**scrollStart**

滚动开始时触发，event事件对象包括：

> type：事件类型，字符串类型，固定值：scrollStart；
> 
> target：触发事件的目标组件，dom对象
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型

**scrollChange**

滚动时多次触发，event事件对象包括：

> type：事件类型，字符串类型，固定值：scrollChange；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型

param对象为json对象，定义如下：

> y：y轴滚动位移坐标值，数字类型
> 
> oldY：上次y轴滚动位移坐标值，数字类型

**scrollStop**

滚动结束时触发，event事件对象包括：

> type：事件类型，字符串类型，固定值：scrollStop；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型

**itemClick**

列表项点击时触发，event事件对象包括：

> type：事件类型，字符串类型，固定值：itemClick；
> 
> target：点击item所在的cell对象，dom对象；
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型；
> 
> index：点击item对应的Adapter数据索引，数字类型；

注：target返回dom对象只读。

**leftItemClick**

列表项左侧区域点击时触发，event事件对象包括：

> type：事件类型，字符串类型，固定值：leftItemClick；
> 
> target：点击left区域所在的cell对象，dom对象；
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型；
> 
> index：点击item对应的Adapter数据索引，数字类型；

注：

1：simplelist为滑动列表时支持；

2：target返回dom对象只读


**rightItemClick**

列表项右侧区域点击时触发，event事件对象，包括：

> type：事件类型，字符串类型，固定值：rightItemClick；
> 
> target：点击right区域所在的cell对象，dom对象；
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型；
> 
> index：点击item对应的Adapter数据索引，数字类型；

注：

1：simplelist为滑动列表时支持；

2：target返回dom对象只读；



<h2 id="cid_3">js方法</h2>

本节目录：

> [公共方法](#ff_0)
> 
> [setAdapter(adapter:SimpleListAdapter): void  绑定simplelist容器与SimpleListAdapter对象关系](#ff_1)
> 
> [getAdapter(): SimpleListAdapter  获取simplelist容器绑定的数据对象](#ff_2)
> 
> [scrollTo(jsonData：Object): void 将容器内的当前内容滚动到指定位置](#ff_3)
> 
> [scrollToType(jsonData:Object): void 将容器内的当前内容滚动到特定位置](#ff_4)
> 
> [scrollToPosition(jsonData:Object): void 将 容器内的当前内容滚动到特定索引位置](#ff_5)
> 
> [scrollHeaderToType(jsonData:Object): void 将容器内的header区域滚动到特定位置 ](#ff_6)
> 
> [scrollFooterToType(jsonData:Object): void 将容器内的footer区域滚动到特定位置](#ff_7)
> 
> [scrollBy(jsonData:Object): void 容器基于相对位置滚动](#ff_8)
> 
> [getScrollY(): number 获取滚动容器y轴动点坐标](#ff_9)
> 
> [hideHeader(): void 隐藏列表顶部区域](#ff_10)
> 
> [showHeader(): void 显示列表顶部区域](#ff_11)
> 
> [getHeader(): dom 获取列表header区域](#ff_12)
> 
> [refreshHeader(): void 刷新列表header区域](#ff_13)
> 
> [hideFoodter(): void 隐藏列表底部区域](#ff_14)
> 
> [showFooter(): void 显示列表底部区域](#ff_15)
> 
> [getFooter(): dom 获取列表Footer区域](#ff_16)
> 
> [refreshFooter(): void 刷新列表footer区域](#ff_17)
> 
> [setCaptureTouchEvent(captureTouchEvent:boolean): void 设置滚动容器是否拦截子组件touch事件](#ff_18)
> 
> [getCaptureTouchEvent(): boolean 获取滚动容器是否拦截子组件touch事件](#ff_19)
> 
> [resetItem(): void 收回列表中展开的滑动区域](#ff_20)



<span id="ff_0"><code>**公共方法**</code></span>   

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


<span id="ff_1">**setAdapter(adapter:SimpleListAdapter): void**</span>  

<code>绑定simplelist容器与SimpleListAdapter对象关系</code>  

参数：

adapter：需要绑定的SimpleList显示数据，SimpleListAdapter类型；   

返回值：无

<span id="ff_2">**getAdapter() :SimpleListAdapter**</span>

<code>获取simplelist容器绑定的数据对象</code>

参数：无

返回值：simplelist容器绑定的数据对象，SimpleListAdapter类型，若未绑定则返回null。


<span id="ff_3">**scrollTo(jsonData:Object): void**</span>

<code>将容器内的当前内容滚动到指定位置</code>

参数：

jsonData：滚动参数，json对象，定义如下：

> y：需要滚动y坐标，数字，竖向滚动容器设置；
> 
> animated：滚动时是否启用动画，bool型，可选项，true：启用动画；false：不启用动画；（默认）

返回值：无

<span id="ff_4">**scrollToType(jsonData:Object): void**</span>

<code>将容器内的当前内容滚动到特定位置</code>

参数：

jsonData：滚动参数，json对象，定义如下：

> scrollType：滚动位置，字符串枚举型，必选项，【top，middle，bottom】
> - top：跳转到容器顶部；
> - middle：跳转到容器内容中间；
> - bottom：跳转到容器底部。 
> - animated：滚动时是否启用动画，bool型，可选项，true：启用动画；false：不启用动画（默认）；

返回值：无

<span id="ff_5">**scrollToPosition（jsonData:Object): void**</span>

<code>将容器内的当前内容滚动到特定索引位置</code>

参数：

jsonData：滚动参数，json对象，定义如下：

> index：需要滚动至item索引，必选项；
> 
> animated：滚动时是否启用动画，bool型，可选项，true：启用动画；false：不启用动画（默认）
> 
> scrollType：滚动位置，字符串枚举型，可选项，【top，bottom】
> - top：item区域顶边与容器顶边对齐；（默认）
> - bottom：item区域底边与容器底边对齐；

返回值：无


<span id="ff_6">**scrollHeaderToType(jsonData:Object): void**</span>

<code>将容器内的header区域滚动到特定位置</code>

参数：

jsonData：滚动参数，json对象，定义如下：

> scrollType：滚动位置，字符串枚举型，必选项，【top，bottom】
> - top：header区域顶边与容器顶边对齐；
> - bottom：header区域底边与容器底边对齐；
> 
> animated：滚动时是否启用动画，bool型，可选项，true：启用动画；false：不启用动画（默认）；

返回值：无

注：当header区域小于容器显示区域时，scrollType设置为bottom调用失效

 
<span id="ff_7">**scrollFooterToType(jsonData:Object): void**</span>

<code>将容器内的footer区域滚动到特定位置</code>

参数：

jsonData：滚动参数，json对象，定义如下：

> scrollType：滚动位置，字符串枚举型，必选项，【top，bottom】
> - top：footer区域顶边与容器顶边对齐；
> -bottom：footer区域底边与容器底边对齐；
> 
> animated：滚动是是否启用动画，bool型，可选项，true:启用动画；false：不启用动画（默认）；

返回值：无

注：当footer区域小于容器显示区域时，scrollType设置为top调用失效

<span id="ff_8">**scrollBy(jsonData:Object): void**</span>

<code>容器基于相对位置滚动</code>

参数：

jsonData：滚动参数，json对象，定义如下：

> y：需要滚动y坐标方向上相对位移，数字，竖向滚动容器设置；
> 
> animated：滚动时是否启用动画，bool型，true：启用动画，false：不启用动画；

返回值：无

<span id="ff_9">**getScrollY(): number**</span>

<code>获取滚动容器y轴动点坐标</code>

参数：无

返回值：滚动容器y轴滚动点坐标，竖向滚动容器使用

<span id="ff_10">**hideHeader(): void**</span>

<code>隐藏列表顶部区域</code>

参数：无

返回值：无

<span id="ff_11">**showHeader(): void**</span>

<code>显示列表顶部区域</code>

参数：无

返回值：无

<span id="ff_12">**getHeader(): dom**</span>

<code>获取列表header区域</code>

参数：无

返回值:header区域dom对象

<span id="ff_13">**refreshHeader():void**</span>

<code>刷新列表header区域</code>

参数：无

返回值：无

<span id="ff_14">**hiderFooter():void**</span>

<code>隐藏列表底部区域</code>

参数：无

返回值：无

<span id="ff_15">**showFooter(): void**</span>

<code>显示列表底部区域</code>

参数：无

返回值：无

<span id="ff_16">**getFooter(): dom**</span>

<code>获取列表Footer区域</code>

参数：无

返回值：footer区域dom对象

<span id="ff_17">**refreshFooter(): void**</span>

<code>刷新列表footer区域</code>

参数：无

返回值：无

<span id="ff_18">**setCaptureTouchEvent(captureTouchEvent：boolean): void**</span>

<code>设置滚动容器是否拦截子组件touch事件</code>

参数： 

captureTouchEvent：滚动容器是否拦截子组件touch事件，bool型。
> true: 拦截子组件touch事件
> false：不拦截子组件touch事件

返回值：无

注：默认拦截子组件touch事件

<span id="ff_19">**getCaptureTouchEvent(): boolean**</span>

<code>获取滚动容器是否拦截子组件touch事件</code>

参数：无

返回值：滚动容器是否拦截子组件touch事件，bool型
> true：拦截子组件touch事件
> false：不拦截子组件touch事件

注：默认拦截子组件touch事件

<span id="ff_20">**resetItem(): void**</span>

<code>收回列表中展开的滑动区域</code>

参数：无

返回值：无

注：simplelist为滑动列表时支持