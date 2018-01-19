# UmengMtj 友盟统计组件

-------

UmengMtj封装了友盟统计SDK功能支持，应用使用该组件可快速与友盟统计服务器对接，对应用使用及关键功能进行统计。

UmengMtj为外置组件。

<h2 id="cid_1">方法</h2>

本节目录：

> [onPageStart(jsonData:Object):void 页面激活是调用该方法](#ff_0)
> 
> [onPageEnd(jsonData:Object):void 页面非激活时调用该方法](#ff_1)
> 
> [onEvent(jsonData:Object):void 上报自定义事件](#ff_2)
> 
> [setCatchUncaughtExceptions(isCatch:boolean):void 设置开启或关闭崩溃错误日志上报](#ff_3)


<span id="ff_0">**onPageStart(jsonData:Object):void**</span>

<code>页面激活是调用该方法</code>

参数：

jsonData：设置参数，json格式，定义如下：

> pageName：需要统计自定义页面名称，字符串类型

返回值：无

注：为保证统计正确性，该方法应用再页面window组件的resume回调中；


<span id="ff_1">**onPageEnd(jsonData:Object):void**</span>

<code>页面非激活时调用该方法</code>

参数：

jsonData：设置参数，json格式，定义如下：

> pageName：需要统计自定义页面名称，字符串类型

返回值：无

注：为保证统计正确性，该方法应用再页面window组件的pause回调中；


<span id="ff_2">**onEvent(jsonData:Object):void**</span>

<code>上报自定义事件</code>

参数：

jsonData：上传自定义信息，json格式，定义如下：

> id：自定义事件id，字符串，必选项；
> 
> params：当前事件的属性和取值；json类型（key-value）键值对，可选项
> 
> counter：当前事件的数值，数字，可选项

返回值：无

注：使用自定义时间功能请先登录友盟官网，在“统计分析->设置->事件”（子账户由于权限限制可能无法看到“设置”选项，请联系主帐号开通权限。）页面中添加相应的事件id（事件id可用英文或数字，不要使用中文和特殊字符且不能使用英文句号“.”，您可以使用下划线“_”），然后服务器才会对相应的事件请求进行处理。


<span id="ff_3">**setCatchUncaughtExceptions(isCatch:boolean):void**</span>

<code>设置开启或关闭崩溃错误日志上报</code>

参数：

isCatch：开启/关闭错误日志上报，bool型。true：错误日志上报开启；（默认）；false：错误日志上报关闭；

返回值：无

