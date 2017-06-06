# 公共样式

----------

Sprite盒模型基于 CSS 盒模型，每个UI组件均可视作一个盒子，如下图所示：  

<img  src="image/ggys_1.png" />    

<h2 id="cid_0">取值说明</h2>

**Color颜色**   

Sprite支持多种取值类型，具体描述如下：    
 
> RGB（rgb(255, 0, 0)）；  
> 
> RGBA（rgba(255, 0, 0, 0.5)）；  
> 
> 十六进制（#rrggbb）；  
> 
> 色值关键字（black|silver|gray|white|red|green|blue|yellow|transparent）；


**绘制单位**  

> dp，全称device independent pixels，一种基于屏幕密度的抽象单位，与设备屏幕有关。在每英寸160点的屏幕上，1dp=1px。在Sprite中，使用dp作为界面元素的尺寸度量单位，double型，使用时可省略dp，直接写数字。  
> 
> 如： style="width:20;border-size:0.5";  


<h2 id="cid_1">尺寸</h2>

**width**   

<code>UI组件宽度 </code>

UI组件宽度，数字，单位dp（可省略），示例：width:50;    

fill_screen用于占满当前屏幕宽度，示例：width:fill_screen;  

**height**  

<code>UI组件高度 </code>  

UI组件高度，数字，单位dp（可省略），示例：height:50;    

fill_screen用于占满当前屏幕高度，示例：height:fill_screen;



<h2 id="cid_2">定位</h2>

**position** 

<code>定位模式 </code>

取值 [relative ,absolute]  

> relative：生成相对定位的元素，相对于其正常布局位置进行定位。（默认）；  
> 
> absolute：生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位；

**top**  

<code>距离上方的偏移量</code>   

取值数字，默认为 0；


**bottom**   

<code>距离下方的偏移量</code>

取值数字，默认为 0；

**left**  

<code>距离左方的偏移量</code>

取值数字，默认为 0；


**right**    

<code>距离右方的偏移量</code>

取值数字，默认为 0；

**注：**

- 当控件为布局为绝对定位时，其位置相对于父容器的绝对位置。

- 布局为绝对定位时，如果没有直接给出width和height，其容器大小需要通过设定top、left、right和bottom来限制大小。


<h2 id="cid_3">内边距</h2>

**padding**   

<code>UI组件内边距</code>

UI组件内边距，上 右 下 左 ，默认 0 0 0 0， 示例：padding:5 5 5 5 

值为一个时表示四边，示例：padding:5;   




**padding-left**  

<code>UI组件内左边距</code> 

取值数字，默认 0， 示例：padding-left:5;


**padding-right**  

<code>UI组件内右边距</code> 

取值数字 ，默认 0， 示例：padding-right:5;


**padding-top**  

<code>UI组件内顶边距</code> 
 
取值数字 ，默认 0， 示例：padding-top:5;


**padding-bottom**  

<code>UI组件内底边距</code> 

取值数字，默认 0， 示例：padding-bottom:5;



<h2 id="cid_4">边框</h2>

**border-style**  

<code>边框样式</code> 

取值 [solid,dashed,dotted]  

> solid：定义实线（默认）  
> 
> dashed：定义虚线    
> 
> dotted：定义点状边框  


**border-color**    

<code>边框色</code> 

取值参考color取值说明，默认transparent  

**border-width**   

<code>边框宽度</code>

取值数字，默认0dp  

**border-radius**  

<code>边框弧度</code>

取值数字 ，默认0  

**border-bottom-left-radius**

<code> 左下边框弧度</code>

取值数字，默认0  

**border-bottom-right-radius**  

<code> 右下边框弧度</code>

取值数字 ，默认0  

**border-top-left-radius**  

<code> 左上边框弧度</code>

取值数字，默认0  

**border-bottom-left-radius**  

<code> 左下边框弧度</code> 

取值数字，默认0


<h2 id="cid_5">背景</h2>

**background-color**  

<code> 设置背景色</code> 

取值参考color取值说明，默认值transparent透明色；  

**opacity**   

<code>组件透明度</code> 

取值数字，取值范围为 [0, 1]

> 1，即完全不透明（默认值）；
> 
> 0 是完全透明；0.5 是 50% 的透明度；  

**注：**   opacity设置的是整个控件的透明，如果控件是容器，那么容器内部所有的控件都会跟着一起变透明。如果想实现背景色透明，可以使用background-color:rgba(rgba(255, 0, 0, 0.5))来设置。    

<h2 id="cid_6">文本样式</h2>

文档类组件共享一些共同特性, 如：text，textfiled，textarea；  

**color**  

<code>文字颜色</code>

取值参考color取值说明，默认值#333333；  

**font-size**  

<code>文字大小</code>

取值数字，单位dp，默认16  

**font-style** 

<code>字体类别</code>

取值 [normal,italic] 

>  normal：普通字体（默认）；
> 
>   italic：斜体；  

**font-weight** 

<code>字体粗细程度</code> 

取值 [normal,bold]  
 
>   normal：正常字体（默认） ； 
>  
>   bold：粗体；  


**text-decoration**   

<code>字体装饰样式</code> 

取值 [none,underline,line-through]  
 
>   none: 无装饰（默认）；  
> 
>   underline：文字装饰为下划线；  
> 
>  line-through：文字装饰为中间贯穿线；  


**text-align**

<code>文字水平方向对齐方式</code> 

取值 [left,center,right]
 
>  left：文本水平方向左对齐；（默认）
> 
>  center：文本水平方向居中对齐；
> 
>  right：文本水平方向右对齐；


**text-overflow**  

<code>内容超长时文本省略样式</code> 

取值 [clip,ellipsis]

>  clip：省略无法显示文本（默认）；
> 
>  ellipsis：显示省略符号来代表被裁剪的文本；

**注：**   如果想设置文字为省略样式，首先必须设置文本单行显示，如text样式singleline：true，并且text宽度应该小于等于父容器的宽度。  


<h2 id="cid_7">显影</h2> 

**display**  

<code>控件是否显示</code> 

取值字符串枚举型 [block,none] 
 
>  block：显示；
> 
>  none：隐藏，且不分配占位空间，
 
**注：** 使用该属性显隐控件后，需要调用document.refresh()刷新布局；  


**visibility**  

<code>控件是否可见</code> 

取值字符串枚举型， [visible, hidden]  

>  visible：显示； 
> 
>  hidden：隐藏，分配占位空间，不需要document.refresh()进行布局刷新;  

**注：**   在使用显影控制时，如果不涉及整个页面布局变动，建议用visibility来做显影，这样就不要刷新布局，提高显影效率。那么什么情况下是布局变动呢，比如隐藏一个控件后，这个控件下面的控件都会网上移动，这种情况下需要使用document.refresh()刷新页面布局。  

<h2 id="cid_8">flexbox布局</h2>

参考 [flexbox布局原理](https://gitdocument.exmobi.cn/sprite-api/flexbjyl.html)  
