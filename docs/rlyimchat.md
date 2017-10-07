# rlyimchat 组件使用   

------

rlyimchat 控件主要用于使用IM功能时，聊天窗口界面展现，如下图所示：

<img  width="250" src="image/rlyimchat_1.png"/>

rlyimchat控件考虑支持以下功能：  

1：rlyimchat控件需要在edn打包时勾选IM选项方可正常使用；  

2：rlyimchat控件为全屏控件；  

3：rlyimchat控件UI包括：聊天区域及输入区域，分布说明如下：  

   聊天区域：消息时间，本人头像，聊天人头像，聊天人姓名，聊天内容（文本，语音，图片，文件，表情）；   

   输入区域：语音/文本输入方式切换，文本输入框，表情选择，语音输入，图片选择，拍照选择，文件选择（仅Android）；  

4：rlyimchat控件提供设置聊天人id（voipId）的js方法，用于开发人员设置聊天人id；  

5： 当登录成功并设置正确聊天人id后启动rlyimchat聊天界面后，会自动接收，监听消息，并在聊天区域中展现；

**注：** 该控件必须在IM登录成功后才可以加载显示。

  


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

> [iconClick  点击聊天界面头像触发 ](#sj_1)
>
> [fileClick  点击聊天界面已接收文件时触发 ](#sj_2)
>
> [linkClick  点击聊天界面链接类地址时触发 ](#sj_3)
>
> [messageSendClick  长按聊天信息弹出转发菜单](#sj_4)


<span id="sj_1">**iconClick**</span>  

<code>点击聊天界面头像触发</code>  

event事件对象包括：   

>  type：事件类型,字符串类型,固定值：iconClick
>  
> target：触发事件的目标组件,dom对象
> 
>  timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下： 

> id：该头像对应人员voipId，字符串类型


<span id="sj_2">**fileClick**</span>  

<code>点击聊天界面已接收文件时触发</code>  

event事件对象包括：  

> type：事件类型,字符串类型,固定值：fileClick  
> 
> target：触发事件的目标组件,dom对象  
> 
>timestamp：事件触发的时间戳,单位毫秒,数字类型  

param对象为Json对象,定义如下：  

> fileName：下载文件名称，字符串类型  

> filePath：下载文件保存全路径，字符串类型

**注：** 文件实际名以fileName为准



<span id="sj_3">**linkClick**</span>  

<code>点击聊天界面链接类地址时触发</code>   

event事件对象包括：    

>   type：事件类型,字符串类型,固定值：linkClick  
>   
>   target：触发事件的目标组件,dom对象  
>   
>   timestamp：事件触发的时间戳,单位毫秒,数字类型  

param对象为Json对象,定义如下：  

> url：链接字符串地址，字符串类型  




<span id="sj_4">**messageSendClick**</span>  

<code>长按聊天信息弹出转发菜单</code>   

event事件对象包括：    

>type：事件类型,字符串类型,固定值：messageSendClick  
> 
>target：触发事件的目标组件,dom对象  
>
>timestamp：事件触发的时间戳,单位毫秒,数字类型

param对象为Json对象,定义如下：  

>type：消息类型，字符串枚举型【text，image】，text：文本类型；image：图片类型；
>
>text：文本消息内容，type为text时生效，字符串类型； 
>
>imgPath：图片全路径，type为image时生效，字符串类型； 
>


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




**setConfig(jsonData:object):void**

<code>设置单聊控件参数</code>  

参数：  

jsonData:单聊控件参数，Json格式，格式定义如下：  

> receiverId：对方聊天人voipId，字符串类型，必选参数
> 
>  receiverName：对方聊天人昵称，字符串类型，必选参数

返回值：无  


**注：**  必须在页面加载时调用该方法设置单聊联系人id，否则imchat控件将无法正常使用

**clearMessage()：bool** 

<code>清空聊天信息</code>

参数：无 

返回值：bool型

> true：清空成功
> 
> false：清空失败


<h2 id="cid_4">示例</h2>


无

