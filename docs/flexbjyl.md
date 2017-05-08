# Flex布局原理

----------

Sprite从web中借鉴了Flexbox模式，采用facebook提供的布局库css-layout，Flexbox让常见UI布局构建变的简单，比如按比例划分容器区间，同时支持按内容弹性扩展容器大小。  

<h2 id="cid_0">flexbox布局</h2>

Sprite采用Flexbox布局模型，工作原理和web上的CSS基本一致，可视为子集，以下为详细说明。  

**flex-direction**   

<code> 定义flex 容器中 flex 成员项的排列方向</code>

取值 [row, column]  
 
>  row：从左到右  
> 
>  column：从上到下（默认）  


**flex-wrap**   

<code>水平方向是否进行换行</code>

 定义flex容器中若成员项水平排列超过容器宽度后，是否进行换行，取值 [nowrap, wrap]  
 
>  nowrap：单行显示，不换行（默认）；  
> 
>  wrap：多行显示，支持自动换行；  

**注：**  该样式一般用于水平布局的时候，如果布局容器是垂直布局，默认每个控件必须换行，不能用这个样式，否者可能照成页面无法滚动。


**justify-content**  

<code>容器内成员项在主轴方向上排列方式</code>

定义 flex 容器中 flex 成员项在主轴方向上如何排列，子元素是应该靠近主轴的起始端还是末尾段，亦或应该均匀分布， 取值 [flex-start ,flex-end ,center ,space-between]  

>  flex-start：左对齐（顶对齐），所有的 flex 成员项都排列在容器的前部（默认）；  
> 
>  flex-end：右对齐（底对齐），成员项排列在容器的后部；  
> 
>  center：居中对齐，成员项排列在容器中间、两边留白；  
> 
>  space-between：两端对齐，空白均匀地填充到 flex 成员项之间；


**align-items**  

<code>容器内成员项在交叉轴方向上排列方式</code>

定义 flex 容器中 flex 成员项在交叉轴方向上如何排列，[stretch,flex-start ,center ,flex-end]  
 
>  stretch：拉伸高度至 flex 容器的大小（默认）；  
> 
>  flex-start：上/左对齐，所有的成员项排列在容器顶部；  
> 
>  flex-end：下/右对齐，所有的成员项排列在容器底部；  
> 
>   center：中间对齐，所有成员项都垂直地居中显示；



**align-self**  

<code>单个成员在交叉轴上自有的排列方式 </code>

 定义flex容器中flex单个成员在交叉轴上自有的排列方式，设置后则覆盖父容器align-items属性，取值 [auto,stretch,flex-start ,center ,flex-end]

>   auto：继承父元素的align-items（默认）；  
> 
>   stretch：拉伸高度至 flex 容器的大小；  
>  
>   flex-start：上对齐，所有的成员项排列在容器顶部；  
> 
>   flex-end：下对齐，所有的成员项排列在容器底部；  
> 
>   center：中间对齐，所有成员项都垂直地居中显示；  


**flex**    
 
<code>定义flex容器中 flex 成员项在容器中占据的尺寸</code>

取值数字，如果所有成员项都设置为 flex:1，那么它们就有相等的宽度（水平排列）或者相等的高度（垂直排列）。  

如果一共有两个成员项，其中一个 flex: 1，另一个 flex: 2，那么第一个将占据 1/3 的空间，另一个占据 2/3。如果所有 flex 成员项都不设置 flex 属性，它们将根据容器的 justify-content 属性来决定如何排列。


<h2 id="cid_1">注意问题</h2>

1.	一定要注意在sprite中，最外层容器一定要指定容器大小（高和宽），一般设置全屏大小即可。  

2.	在sprite页面布局中，默认是垂直方向从上往下布局，如果不设置align-items，容器内控件默认会自动填充父容器的宽度（垂直布局填充宽度，水平布局填充高度）。如果设置了align-items除stretch外的其他值，容器内控件的大小将会取决于该控件内容的大小，注意这种情况下line、image、list等一些控件必须给出高和宽（不确定高宽的可以用flex:n来设置区域大小）。  

3.	只有容器自身大小确定后（一般情况下横向要指定宽度，纵向要指定高度），在容器内部才能使用flex:n进行区域分割。  

4.	Sprite中的布局是有层的概念，虽然没有css3那种index-z样式来控制在Z轴层的位置，但是其默认是按照布局来来分层次，在布局方向上，最下面的控件在Z轴上就是最上层，如果有绝对定位控件，建议放在布局容器的最后面。  

5.	如果容器自身是绝对定位控件，那么其自身就不参与父容器的区域分割了，也就是说设置flex:n无效。  
