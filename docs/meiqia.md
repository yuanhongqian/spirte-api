# MeiQia 美洽客服操作组件



---------

移动客服功能考虑集成美洽客服SDK。美洽客服SDK主要包括两部分：客服端及用户端，其中客服端美洽官方已提供安装包可直接使用（可可登陆web系统使用），Sprite主要关注用户端集成。美洽集成说明：[https://meiqia.com/sdk](https://meiqia.com/sdk)，当前最新版本3.4.3。

MeiQia为外置组件。

<h2 id="cid_1">方法</h2>

本节目录：

> [init(jsonData:Object,callFunction:Function):void 初始化MeiQia系统](#ff_0)
> 
> [show(jsonData:Object):void 传入参数，打开美洽客服聊天界面](#ff_1)




<span id="ff_0">**init(jsonData:Object,callFunction:Function):void**</span>

<code>初始化MeiQia系统</code>

参数：

jsonData：美洽初始化参数，json格式定位如下：

> appKey：美洽管理平台申请的应用appKey，字符串类型，可选项，若不设置则使用EDN打包配置

callFunction：初始化回调函数，入参json对象，定义如下：

> code：初始化是否成功，数字类型，【0，-1】，0：初始化成功；-1：初始化失败；
> 
> clientId：初始化成功后，美洽系统分配的用户id，字符串类型；

返回值：无

注：该方法建议在应用启动时调用


<span id="ff_1">**show(jsonData:Object):void**</span>

<code> 传入参数，打开美洽客服聊天界面</code>

参数：

jsonData：启动美洽客服聊天界面传入参数，josn格式定位如下：

> onlineConfig：设置分配客服相关配置，json格式，可选项，包括：
> 
> - agentId：在美洽系统中客服对应的ID，若不设置则系统自动分配客服，字符串类型，可选项，agentId值可以通过管理员帐号在后台查看；
> 
> - groupId：在美洽系统中客服组对应的ID，若不设置则系统自动分配，可选项；
> 
> - rule：客服分配规则，字符串枚举型，取值【none，group，enterprise】
> 
>  - none：指定分配客服不在线时，不转接给任何人；
>  
>  - group：指定分配客服不在线时，转接给组内其他客服；
>  
>  - enterprise：指定分配客服不在线时，转接给其他在线客服；
>  
> userInfo：设置聊天用户信息，将会显示给客服人员，json格式，可选项，包括：
> 
> - name：用户姓名，字符串类型，可选；
> 
> - gender：性别，字符串枚举，【男，女】，可选项；
> 
> - age：年龄：字符串类型，可选项；
> 
> - tel：电话，字符串类型，可选项；
> 
> - weixin：微信号，字符串类型，可选项；
> 
> - weibo：新浪微博ID，字符串类型，可选项；
> 
> - address:地址，字符串类型，可选项；
> 
> - email：邮箱，字符串类型，可选项；
> 
> - avatar：头像url地址，字符串类型，可选项；
> 
> - source：来源，字符串类型，可选项；
> 
> - comment：备注，字符串类型，可选项；
> 
> - tags：标签集，必须是企业中已经存在的标签项，可选项
> 
> clientId：设置美洽系统顾客的id，设置成功后该id对应的顾客将会上线，可实现消息漫游，字符串类型，可选项；
> 
> customizedId：设置开发者系统自定义id，设置成功后将会以该自定义id对应的顾客上线，可实现消息漫游，字符串类型，可选项；
> 
> preSendTextMessage：设置与发送消息，该消息将会在用户上线之后自动发送给客服，可以用于标记客户当前正在浏览的内容等客服需要了解的信息，可选项；

返回值：无

注：
>     1：json格式参数里不能包含英文单引号'，双引号字符串"，若有请先做转义；
>     2：clientId字段与customizedId字段不应同时使用，应根据应用场景选择；    
   
