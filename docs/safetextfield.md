# safetextfield组件使用 

----------

银行/证券/财务等高安全性程序，密码输入时对安全性要求高，使用系统输入法存在一些安全性问题，客户端程序未使用键位随机变化的软键盘来保护登录密码的输入安全。可能存在截屏攻击/键盘劫持等问题，考虑实现安全键盘功能。

安全输入控件定位为安全输入用户密码，控件定义如下：
1：输入框为密码输入框

2： 点击输入框后弹出自定义安全键盘，而非系统输入法

3：自定义输入法支持phone及pad，不就保持一致；

4：自定义输入法支持竖屏/横屏,并支持横竖屏切换；

5：自定义输入法从底部弹出，弹出动画为从下到上，关闭动画为从上到下；

6：自定义输入法弹出后，需要保持编辑框可见，即与目前编辑框输入法弹出类似；

7：自定义输入法分为：数字，字母，符号三种，不支持中文输入；

8：自定义输入法支持设置，默认启动字母模式；

9：自定义输入法顶部tab为输入法切换区域，支持数字，字母，符号切换；

10： 输入法弹出后，点击空白区域或者完成按钮，关闭输入法，点击删除按钮，删除编辑框输入数据，字母模式下，点击caps键进行，字母大小写切换；

11：点击自定义输入法面板外部区域或点击 完成 按钮，关闭输入法；

12：数字模式下，数字分布不是固定的，每次启动随机调换数字位置。

safetextfield安全文本输入组件允许用户通过自定义安全键盘输入文本的基本组件，单行输入密码模式。

**安全键盘为外置UI组件**


<h2 id="cid_0">属性</h2> 

本节目录：  

> [公共属性](#sx_1)
> 
>[ name  控件名称](#sx_2)
> 
>[ sipreturntext  安全键盘弹出后，return键盘显示文字](#sx_3)
>  
> [keyboardType  弹出输入法键盘类型](#sx_4)
>   
> [sipspacetext  安全键盘弹出后，字母模式下空格键显示文字](#sx_5)
>     
> [prompt  提示语](#sx_7)
>   
> [value  文本内容](#sx_8)
>   
> [maxLength  输入字符的最大长度](#sx_9)   
>   
> [disabled  是否禁用该控件](#sx_11)
>   
>[ clearButtonMode  文本框右侧“清除”按钮显示模式 ](#sx_12) 



<span id="sx_1">**公共属性**</span>  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-api/ggsx.html)，包括：id、style、class；



<span id="sx_2">**name**</span>    

<code>控件名</code>  

用于表单提交，字符串类型


<span id="sx_4">**keyboardType**</span>  

<code>弹出输入法键盘类型</code>    

字符串枚举型，【default，number】  

> default：字母模式；（默认）
> 
> number：数字键盘模式；
 


<span id="sx_7">**prompt**</span>  

<code>提示语</code>   

字符串类型，用户没有输入任何内容时，显示的字符串，用户点击输入时，自动置空。  


<span id="sx_8">**value**</span>  

<code>默认文本内容</code>    

字符串类型


<span id="sx_9">**maxLength**</span>  

<code>输入字符的最大长度</code>    

数字类型

  
<span id="sx_11">**disabled**</span>  

<code>是否禁用该控件</code>     

是否禁用该控件，不可编辑【true，false】  

> true：控件为禁用状态；
> 
> fasle：控件为普通状态；（默认）



<span id="sx_12">**clearButtonMode**</span>  

<code>文本框右侧“清除”按钮显示模式</code>   

取值【never，whileEditing，unlessEditing，always】

> never：从不出现；（默认）
> 
> whileEditing：编辑状态时出现；
> 
> unlessEditing：除了编辑状态外都出现；
> 
> always：一直出现；

**注：** 仅iOS系统支持


<span id="sx_3">**sipreturntext**</span>  

<code>return键盘显示文字</code>   

安全键盘弹出后，return键盘显示文字，默认“完成”


<span id="sx_5">**sipspacetext**</span>  

<code>字母模式下空格键显示文字</code>    

安全键盘弹出后，字母模式下空格键显示文字，默认“安全键盘”


<h2 id="cid_1">样式</h2>

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-api/ggys.html)，包括：  
 
> 尺寸
> 
> 定位 
> 
> 内边距：padding:12 8 12 18
> 
> 外边距
> 
> 边框
> 
> 背景
>
>文本样式：color，font-size，font-style，font-weight，text-align 
> 
> flexbox布局：align-self，flex


**prompt-color**  

<code>提示文字颜色</code>

默认值：#aaaaaa
  


**border-color-focus**  

<code>编辑框激活状态下border边框色</code>  

默认值：transparent



<h2 id="cid_2">事件</h2>


**focus**  

<code>获取焦点，进入编辑状态时触发</code>    

进入编辑状态时触发，event事件对象包括：  

> type：事件类型，字符串类型，固定值：focus；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型



**blur**  

<code>失去焦点，退出编辑状态时触发</code>    

退出编辑状态时触发，event事件对象包括：  

> type：事件类型，字符串类型，固定值：blur；  
> 
> target：触发事件的目标组件，dom对象；  
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型


**textChanged**

<code>文本框激活状态下，输入值改变时触发</code>   

文本框激活状态下，输入值改变时触发，event事件对象包括：  

> type：事件类型，字符串类型，固定值：textChanged；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

value：改变后的输入值，字符串类型



**return**  

<code>点击输入法“完成”键时触发</code>

vent事件对象包括：  

> type：事件类型，字符串类型，固定值：return；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型


<h2 id="cid_3">js方法</h2>

本节目录：

> [公共方法](#ff_0)
> 
> [setFocus(): void  设置当前编辑框获取焦点](#ff_1)
> 
> [isFocus(): boolean  当前编辑框是否获取焦点](#ff_2)
> 
> [clear(): void;](#ff_3)

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


<span id="ff_1">**setFocus(): void**</span>  

<code>设置当前编辑框获取焦点</code>  

参数：无   

返回：无


<span id="ff_2">**isFocus(): boolean**</span>   

<code>当前编辑框是否获取焦点</code>    

参数：无  

返回值：是否获取焦点，bool型  

> true：编辑框已获取焦点
> 
> false：编辑框未获取焦点



<span id="ff_3">**clear(): void**</span>   

<code>清空输入框内容</code>    

参数：无  

返回值：无  





 


