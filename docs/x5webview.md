# x5webview组件使用 

----------

x5webview集成了腾讯X5内核，用于屏蔽Android原生webview系统差异性，关于腾讯X5引擎介绍见[https://x5.tencent.com/tbs/guide/sdkInit.html](https://x5.tencent.com/tbs/guide/sdkInit.html)，仅Android支持。

X5引擎采用动态加载机制，即只有当设备和网络环境满足X5引擎的加载要求时，才会使用X5引擎，若加载失败或者加载异常则自动切换至系统webview，下面描述下X5内核启用流程。

1：如果手机上未安装微信，手Q或者QQ浏览器，接入X5应用会自己去下载X5内核，并在应用重启后启用；

2：如果手机上安装了手Q或者微信或者浏览器，则会去寻找共享的X5内核，而不会自己下载新X5内核；

3：如果手Q或者微信没打开过网页，则内核还是不会启用，需要先手动点开网页；

4：如果应用依赖的是手Q的内核，在手Q被卸载之后，应用会去寻找其他共享X5内核，走第2步；

辨别是否使用x5webview的方法，显示网页文字时，可通过长按选择文字的标识判断，如下水滴状选择效果是x5webview的标志，如下图所示。

<image src="image/x5webview_1.png"/>

x5webview为外置组件。



<h2 id="cid_1">属性</h2>   


**公共属性**  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-api/ggsx.html)，包括：id、style、class；  


**url**  

<code>浏览器控件需加载页面地址</code>

支持本地页面方式加载（res:  , file:）,也支持网络页面方式加载(http://) 


**bridge**  

<code>是否注入桥接Api</code>   

注入后可在浏览器中使用本地能力Js函数，[true，false]

> true：注入桥接Api  
> 
> false：不注入（默认）


**zoom**  

<code>浏览器加载页面是否支持缩放</code>   

取值 [true，false ]  

> true：支持缩放  
> 
> false：不支持缩放（默认）


**checkSsl**  

<code>访问https网站时是否校验ssl证书</code> 

取值 [true，false]  

> true：校验ssl证书 （默认）
> 
> false：不校验ssl证书  

**注：** 仅Android支持，iOS固定校验ssl证书 



**progress**  

<code>网络url加载时顶部进度条是否显示</code>  

取值  [true，false] 

> tue：网络url加载时显示顶部进度条（默认）
> 
> false：网络url加载时不显示顶部进度条




<h2 id="cid_2">样式</h2>  

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-api/ggys.html)，包括：  
 
> 尺寸
> 
> 定位 
>  
> 外边距
> 
> flexbox布局：align-self，flex


**progress-color**  

<code>进度条颜色</code>  

默认值：#00bf12




<h2 id="cid_3">事件</h2>


**plusready**  

<code>页面加载完成后触发</code>

event事件对象包括：   

> type：事件类型，字符串类型，固定值：plusready
> 
> target：触发事件的目标组件，dom对象
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型



**failed**  

<code>页面加载失败后触发</code>  

event事件对象包括： 
  
> type：事件类型，字符串类型，固定值：failed
> 
> target：触发事件的目标组件，dom对象
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型




**titleChange**  

<code>x5webview页面加载url，若标题更新则触发回调函数</code>    

event事件对象包括：    

> type：事件类型，字符串类型，固定值：titleChange
> 
> target：触发事件的目标组件，dom对象
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param对象为Json对象，定义如下：  

> title：当前页面标题，字符串类型 
> 
> url：当前页面url，字符串类型


<h2 id="cid_4">js方法</h2>   

本节目录：

> [公共方法 ](#ff_1)
> 
> [executeScript(scriptText:string): void   执行x5webview控件加载html页面js脚本](#ff_2)  
> 
> [clearCache(): void   清理x5webview浏览器缓存 ](#ff_3)
> 
> [canBack(): boolean   基于已打开html页面是否支持回退  ](#ff_4)
> 
> [back(): void   基于已打开html页面回退](#ff_5)
> 
> [canForward(): boolean  基于已打开html页面是否支持前进](#ff_6)
> 
> [forward (): void  基于已打开html页面前进](#ff_7)



<span id="ff_1"><code>**公共方法**</code></span>  

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
> [setClassStyle(className:string,domobj:IElement): void   设置节点对应Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_16) 
>  
> [getClassStyle(): string  获取节点已设置Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.htm#ptdom_17)  
>  
> [getTag(): string  获取UI组件类型](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_18)  
>  
> [getId(): string  获取UI组件Id标识](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_19) 


<span id="ff_2">**executeScript(scriptText:string): void**</span>  

<code>执行x5webview控件加载html页面js脚本</code>  

参数：  

scriptText：需要执行x5webview控件内（page内）脚本方法，必选项，支持传递字符串类型变量

返回值：无


<span id="ff_3">**clearCache(): void**</span>  

<code>清理x5webview浏览器缓存</code> 

参数：无 

返回值：无


<span id="ff_4">**canBack(): boolean**</span>  

<code>基于已打开html页面是否支持回退</code>   

参数：无  

返回值：bool型 

> true：支持回退
> 
> false：不支持回退



<span id="ff_5">**back(): void**</span>  

<code>基于已打开html页面回退</code>    

参数：无 

返回值：无


<span id="ff_6">**canForward(): boolean**</span>  

<code>基于已打开html页面是否支持前进</code>  

参数：无  

返回值：bool型  

> true：支持前进
> 
> false：不支持前进


<span id="ff_7">**forward (): void**</span>  

<code>基于已打开html页面前进</code>  

参数：无  

返回值：无


<h2 id="cid_5">内置对象</h2>   

内置NativePage对象用于实现x5webview内调用外部uixml页面JS。

**executeScript(scriptText:string):void** 

<code>x5webview控件内部调用外部uixml页面JS</code>  

参数：

scriptText：需要执行外部uixml页面脚本方法，必选项，字符串类型

返回值：无

内置Sprite对象用于实现桥接功能。

**require(moduleName:string): object**

<code>x5webview控件实现对系统api对象引用</code>

参数：

moduleName：待引用模块标识，必选项，字符串

返回值：模块对象，js对象


<h2 id="cid_6">桥接功能</h2>   

通过Sprite.require("模块标识")来实现对系统api对象引用，如使用Device对象方法。

````
var device = Sprite.require("Device");
var version = device.getVersion();
````

**支持桥接组件**

<code>内置功能组件</code>

> [App](https://gitdocument.exmobi.cn/sprite-api/app.html)
> 
> [Window ](https://gitdocument.exmobi.cn/sprite-api/window.html)注：
> - 方法不支持：hideSip();
> - 事件不支持：loader，animator
> 
> [Device](https://gitdocument.exmobi.cn/sprite-api/device.html)
> 
> [Native](https://gitdocument.exmobi.cn/sprite-api/native.html)
> 
> [Encryption](https://gitdocument.exmobi.cn/sprite-api/encryption.html)
> 
> [Time](https://gitdocument.exmobi.cn/sprite-api/time.html)
> 
> [Http](https://gitdocument.exmobi.cn/sprite-api/http.html)
> 
> [NetInfo](https://gitdocument.exmobi.cn/sprite-api/netinfo.html)
> 
> [File](https://gitdocument.exmobi.cn/sprite-api/file.html)
> 
> [UI](https://gitdocument.exmobi.cn/sprite-api/ui.html)
> [MemCache](https://gitdocument.exmobi.cn/sprite-api/memcache.html)
> 
> [DiskCache](https://gitdocument.exmobi.cn/sprite-api/diskcache.html)
> 
> [Camera](https://gitdocument.exmobi.cn/sprite-api/camera.html)
> 
> [Console](https://gitdocument.exmobi.cn/sprite-api/console.html)
> 
> [Pixel](https://gitdocument.exmobi.cn/sprite-api/pixel.html)
> 
> [ImageUtil](https://gitdocument.exmobi.cn/sprite-api/imageutil.html)
> 
> [Location](https://gitdocument.exmobi.cn/sprite-api/location.html)


<code>外置功能组件</code>

> [Db](https://gitdocument.exmobi.cn/sprite-api/db.html)
> 
> [DbCipher](https://gitdocument.exmobi.cn/sprite-api/dbcipher.html)
> 
> [Barcode](https://gitdocument.exmobi.cn/sprite-api/barcode.html)
> 
> [XmlDocument](https://gitdocument.exmobi.cn/sprite-api/xmldocument.html)
> 
> [XmlElement](https://gitdocument.exmobi.cn/sprite-api/xmlelement.html)
> 
> [AccessAuth](https://gitdocument.exmobi.cn/sprite-api/accessauth.html)
> 
> [VideoUtil](https://gitdocument.exmobi.cn/sprite-api/videoutil.html)
> 
> [Phone](https://gitdocument.exmobi.cn/sprite-api/phone.html)
> 
> [Sms](https://gitdocument.exmobi.cn/sprite-api/sms.html)
> [Contact](https://gitdocument.exmobi.cn/sprite-api/contact.html)
> 
> [AudioPlay](https://gitdocument.exmobi.cn/sprite-api/audioplay.html)
> 
> [AudioRecord](https://gitdocument.exmobi.cn/sprite-api/audiorecord.html)
> 
> [MapUtil](https://gitdocument.exmobi.cn/sprite-api/maputil.html)
> 
> [IapPay](https://gitdocument.exmobi.cn/sprite-api/iappay.html)
> 
> [WeiXin](https://gitdocument.exmobi.cn/sprite-api/weixin.html)
> 
> [Qq](https://gitdocument.exmobi.cn/sprite-api/qq.html)
> [WeiBo](https://gitdocument.exmobi.cn/sprite-api/weibo.html)
> 
> [BaiduLocation](https://gitdocument.exmobi.cn/sprite-api/baidulocation.html)
> 
> [AliPay](https://gitdocument.exmobi.cn/sprite-api/alipay.html)
> 
> [BaiduVoice](https://gitdocument.exmobi.cn/sprite-api/baiduvoice.html)
> 
> [BaiduTts](https://gitdocument.exmobi.cn/sprite-api/baidutts.html)
> 
> [SanforVpn](https://gitdocument.exmobi.cn/sprite-api/sangforvpn.html)
> 
> [ExMobiPush](https://gitdocument.exmobi.cn/sprite-api/exmobipush.html)