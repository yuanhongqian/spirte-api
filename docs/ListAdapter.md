# ListAdapter组件使用 

----------

ListAdapter为list容器提供高性能的数据处理和访问，ListAdapter本身并不保存数据，二次开发人员重写getView，getCellId，getItem，getCount返回展现的相关数据，实时展现在list容器上。  

再试用ListAdapter组件的时候，需要在js里面导入：  

```javascript
 var Adapter = require("ListAdapter");
```



<h2 id="cid_3">事件</h2>

本节目录：

> [ getView  list容器绘制 ](#sj_1) 
> 
> [ getCellId  返回对应模板id ](#sj_2)
> 
>[ getCount  返回列表总行数](#sj_3)
>
>[ getSectionCount  返回section栏总数](#sj_4)
>
>[getSectionText   返回指定section栏所显示的文字](#sj_5)

**注：** 事件中的 返回值 是开发者需要return的返回值。

<span id="sj_1">**getView**</span>   

<code>list容器绘制</code>    

数据同list容器绑定后，当item节点需要绘制时触发，二次开发人员在该函数中设置view所需相关参数给list容器绘制。  

event事件对象包括：    

> type：事件类型，字符串类型，固定值：getView；
> 
> target：需要设置的item节点，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

index：该item对应的ListAdapter数据索引，数字类型

sectionIndex：该item对应的section索引，数据类型，普通列表返回0


<span id="sj_2">**getCellId**</span>  

<code>返回对应模板id</code>    

数据同list容器绑定后，当item节点需要绘制时触发，二次开发人员在该函数中返回对应模板id

event事件对象包括：    

> type：事件类型，字符串类型，固定值：getCellId；
> 
> target：固定返回null；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

index：该item对应的ListAdapter数据索引，数字类型 

sectionIndex：该item对应的section索引，数据类型，普通列表返回0；

返回值：对应cell模板id值，字符类型

**注：** 该回调事件主要用于多模板展现，二次开发人员需要返回cell模板id，若单模板则可不实现回调



<span id="sj_3">**getCount**</span>

<code>返回列表总行数</code>     


数据同list容器绑定后，当item节点需要绘制时触发，二次开发人员在该函数中返回列表总行数 

event事件对象包括：    

> type：事件类型，字符串类型，固定值：getCount；
> 
> target：固定返回null；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

sectionIndex：section索引，数字类型，普通列表固定返回0；

返回值：section组所包含的item个数




<span id="sj_4">**getSectionCount**</span>

<code>返回section栏总数</code>    

event事件对象包括：    

> type：事件类型，字符串类型，固定值：getCount；
> 
> target：固定返回null；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

返回值：section组总数，数字类型，普通列表固定返回1；



<span id="sj_5">**getSectionText**</span>

<code>返回指定section栏所显示的文字 </code>


数据同list容器绑定后，当item节点需要绘制时触发，二次开发人员在该函数中返回指定section栏所显示的文字   

event事件对象包括：    

> type：事件类型，字符串类型，固定值：getCount；
> 
> target：固定返回null；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

sectionIndex：section栏索引，数字类型
 
返回值：指定section栏所显示的文字，普通列表固定返回null；


<h2 id="cid_4">js方法</h2> 

本节目录：

> [refresh(): void 刷新数据并通知list容器更新](#ff_1)
> 
> [notifyItemRangeInserted(jsonData:Object): void  插入列表数据后通知list容器局部刷新](#ff_2)
> 
> [notifyItemRangeChanged(jsonData:Object): void  更新列表数据后通知list容器局部刷新](#ff_3)
> 
> [notifyItemRangeRemoved (jsonData:Object): void   移除列表数据后通知list容器局部刷新](#ff_4)

<span id="ff_1">**refresh(): void**</span>

<code>刷新数据并通知list容器更新</code>   
  
参数：无

返回值：无

**注：** 该方法是更新整个list列表所有内容，建议不要经常用该方法更新list内容，可以使用局部刷新来更新list内容，除非整个list内容进行更新。


<span id="ff_2">**notifyItemRangeInserted(jsonData:Object): void**</span>  

<code>插入列表数据后通知list容器局部刷新</code> 

参数： 

jsonData：刷新参数，json格式，定义如下：

> sectionIndex：需刷新 item对应的section索引，数字类型，普通列表设置为0，必选项；
> 
> index：插入item数据索引（0开始计数），数字类型，必选项；
> 
> count：插入item个数，数字类型，可选项，默认为1；
>
>animator：是否启用动画，bool型，可选项，默认false，true：启用动画；false：不启用动画 

返回值：无

**注：**  使用局部插入刷新后，要保证数据源对应进行插入操作，否者可能出错。


<span id="ff_3">**notifyItemRangeChanged(jsonData:Object): void**</span>   

<code>更新列表数据后通知list容器局部刷新</code>  

参数：   

jsonData：刷新参数，json格式，定义如下：  

> sectionIndex：需刷新 item对应的section索引，数字类型，普通列表设置为0，必选项；
> 
> index：更新item数据索引（0开始计数），数字类型，必选项；
> 
> count：更新item个数，数字类型，可选项，默认为1；  

返回值：无

**注：**  使用局部更新刷新后，要保证数据源对应进行修改操作，否者可能出错。


<span id="ff_4">**notifyItemRangeRemoved (jsonData:Object): void**</span>  

<code>移除列表数据后通知list容器局部刷新</code>   

参数：

jsonData：刷新参数，json格式，定义如下：  

> sectionIndex：需刷新 item对应的section索引，数字类型，普通列表设置为0，必选项；
> 
> index：移除item数据索引（0开始计数），数字类型，必选项；
> 
> count：移除item个数，数字类型，可选项，默认为1；  
>
>animator：是否启用动画，bool型，可选项，默认false，true：启用动画；false：不启用动画 


返回值：无

**注：**  使用局部删除刷新后，要保证数据源对应进行删除操作，否者可能出错。  


<h2 id="cid_4">示例</h2>   


[参考list组件示例](https://gitdocument.exmobi.cn/sprite-api/list.html#cid_5)
 






