# rlyimlist组件使用   

------

rlyimlist控件主要用于使用容联云IM功能时，最近联系人列表信息展现

rlyimlist控件支持以下功能：  

> 1：rlyimlist控件需要在edn打包时勾选IM选项方可正常使用；
> 
> 2：rlyimlist控件为全屏控件；  
> 
> 3：rlyimlist列表元素包括：聊天人头像，未读消息条数提示，聊天人名字，最近消息时间，最近消息内容；
> 
> 4：当用户im登录成功后，rlyimlist会自动接收，监听消息时间，并在列表中展现；  

>5：群组列表，元素包括：群组图片（默认固定），未读消息条数提示，群组名称，最近消息时间，最近消息内容（包括发消息人，格式：发消息用户名:消息内容）；  

> 6：群组通知消息：元素包括：通知图片（程序快捷图），未读消息提示，系统通知（首行），通知内容（次行）  

> 7：点击消息列表触发；  


<h2 id="cid_0">属性</h2>

**公共属性**  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-api/ggsx.html)，包括：id、style、class；


<h2 id="cid_1">样式</h2>

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-api/ggys.html)，包括：  

> 尺寸
> 
> 定位
>  
> 外边距
> 
>  
> flexbox布局：align-self,flex


<h2 id="cid_2">事件</h2>

本节目录：

> [notifyClick  点击通知消息触发](#sj_1)  
> 
> [memberClick  点击单聊消息触发](#sj_2)   
> 
> [groupClick  点击群聊消息触发](#sj_3)   
>
> [unreadMessage   监听未读消息](#sj_4)  
>



<span id="sj_1">**notifyClick**</span>  

<code>点击通知消息触发</code>  

event事件对象包括：  

> type：事件类型,字符串类型,固定值：notifyClick
> 
> target：触发事件的目标组件,dom对象
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型



<span id="sj_2">**memberClick**</span>  

<code>点击单聊消息触发</code>  

event事件对象包括：   

> type：事件类型,字符串类型,固定值：memberClick
> 
> target：触发事件的目标组件,dom对象
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下：

> id：成员voipId，字符串类型
> 
> name：成员昵称，字符串类型


<span id="sj_3">**groupClick**</span>  

<code>点击群聊消息触发</code>  

event事件对象包括：

>type：事件类型,字符串类型,固定值：groupClick
>
> target：触发事件的目标组件,dom对象
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型
> 

param对象为Json对象,定义如下：

> id：群组 id，字符串类型
> 
> name：群组名称，字符串类型




<span id="sj_4">**unreadMessage**</span> 

<code>监听未读消息</code>  

event事件对象包括： 

> type：事件类型,字符串类型,固定值：unreadMessage
> 
> target：触发事件的目标组件,dom对象
> 
> timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下：

> total：未读消息总数，包括单聊，群聊，系统通知
> 
> member：单聊未读消息数
> 
> group：群聊未读消息数
> 
> system：系统通知未读消息数；



<h2 id="cid_3">js方法</h2>

**公共方法**  

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

[普通Dom节点操作](https://gitdocument.exmobi.cn/sprite-api/ggff.htmll#cid_3)，包括：  

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
> [setClassStyle(className:string,domobj:IElement): void   设置节点对应Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_16) 
>  
> [getClassStyle(): string  获取节点已设置Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_17)  
>  
> [getTag(): string  获取UI组件类型](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_18)  
>  
> [getId(): string  获取UI组件Id标识](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_19) 




<h2 id="cid_4">示例</h2>


无

