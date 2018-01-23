# FhIm 烽火星空IM工具类

----------

 FhIm为烽火星空IM工具类，提供登录，注销等相关操作方法。



**注：** 该组件为外置组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ login(jsonData:Object,callBackFun:Function): void   启动烽火IM初始化并进行用户登录，处理结果进入回调中返回 ](#ff_0)
> 
> [logout(): void  注销当前已登录IM用户](#ff_1)
> 
> [setSettingInfo (jsonData:Object): void   设置烽火IM服务器设置信息 ](#ff_2)
> 
> [getSettingInfo(): Object 获取烽火IM服务器设置信息](#ff_3)
> 
> [createGroup(jsonData:Object,callFunction:Function): void  创建群组](#ff_4)
> 
> [deleteGroup(jsonData:Object,callbackFun:Function):void 群组删除](#ff_5)
> 
> [modifyGroup(jsonData:Object,callbackFun:Function):void 修改群组信息](#ff_6)
> 
> [inviteGroupMember(jsonData:Object,callbackFun:Function):void 邀请成员加入](#ff_7)
> 
> [deleteGroupMember(jsonData:Object,callbackFun:Function):void 群主踢人/退出](#ff_8)
> 
> [setGroupBlockStatus(jsonData:Object,callbackFun:Function):void 设置自己在群组中屏蔽消息的设置](#ff_9)
> 
> [getGroupInfo(jsonData:Object,callbackFun:Function):void 获取群组消息](#ff_10)
> 
> [groupExists(jsonData:Object,callbackFun:Function):void 检查群组是否存在](#ff_11)
> 
> [getOwnGroup(callbackFun:Function):void 获取用户所属群组](#ff_12)
> 
> [sendText(dataJson:Object,callFunction:Function):void 单聊发送文本](#ff_13)
> 
> [sendImage(dataJson:Object,callFunction:Function):void 单聊发送图片](#ff_14)
> 
> [sendGroupText(dataJson:Object,callFunction:Function):void 群聊发送文本](#ff_15)
> 
> [sendGroupImage(dataJson:Object,callFunction:Function):void 群聊发送图片](#ff_16)


<span id="ff_0">**login(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动烽火IM初始化并进行用户登录，处理结果进入回调中返回</code>  
   

参数：  

jsonData，登录用户传递参数，Json对象，定义如下：  

> userId：烽火Im账号voipId，字符串类型，必选项；
> 
> userName：烽火Im用户名，字符串类型，必选项；
> 
> token：烽火Im账号voip密码，字符串类型，可选项；


callBackFun，登录回调函数，该回调函数具有一个入参，类型为数字：  

> code：数字，0：登录烽火IM服务器成功；-1：登录烽火IM服务器失败；


返回值：无



<span id="ff_1">**logout(): void**</span>

<code>注销当前已登录IM用户</code>    

参数：无


返回值：无



<span id="ff_2">**setSettingInfo (jsonData:Object): void**</span>  

<code>设置烽火IM服务器设置信息</code>   

参数：

jsonData：Json格式，定义如下：  

> ip：im服务器地址，字符串类型
> 
> port：im服务器端口，数字；
> 
> sslPort：im服务器ssl端口，数字。
> 
> isSsl：是否采用加密传输，数字枚举型，0：非加密（默认）；1：加密；
> isVibrate：新消息是否震动，数字枚举型，0：非震动（默认），1：震动
> isSound：新消息是否播放声音，数字。0：不播放（默认），1：播放
> 
> iconUrl：im头像图片请求url地址，字符串；


返回值：无



<span id="ff_3">**getSettingInfo(): Object**</span>  

<code>获取烽火IM服务器设置信息</code> 

参数：无

返回值：json格式，定义如下：

> ip：im服务器地址，字符串类型；
> 
> port：im服务器端口，数字；
> 
> sslPort：im服务器ssl端口，数字；
> 
> isSsl：是否采用加密传输，数字，0：非加密，1：加密（默认）
> 
> iconUrl：im头像图片请求url地址，字符串
> 
> isVibrate：新消息是否震动，数字类型，0：非震动（默认），1：震动
> 
> isSound：新消息是否播放声音，数字。0：不播放（默认），1：播放



<span id="ff_4">**createGroup(jsonData:Object,callFunction:Function): void**</span>  

<code>创建群组</code>  


参数： 

jsonData：登录用户传递数据，json类型，定义如下：

> name：设置群组名称，字符串类型，必选项；
> 
> voipIds：需要邀请的成员，数组类型，数组元素为字符串，可选参数；

callBackFun：创建群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]。0：创建群组成功；-1：创建群组失败；
> 
> groupInfo：创建群组信息，json格式，定义如下：
> 
> - groupId：群组id，字符串类型；
> 
> - name：群组名称，字符串类型；


返回值：无 

<span id="ff_5">**deleteGroup(jsonData:Object,callbackFun:Function):void**</span>

<code>群组删除</code>

参数：

jsonData：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选项参数；

callFunction：解散群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：删除群组成功，-1：删除群组失败 ；
> 
> groupId：群组id，字符串类型；

返回值：无

注：只有群组创建者才能成功调用带接口

<span id="ff_6">**modifyGroup(jsonData:Object,callbackFun:Function):void**</span>

<code>修改群组信息</code>

参数：

jsonData：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选项参数；
> 
> name：设置群组名称，字符串类型，必选参数；

callFunction：修改群组信息回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：修改群组信息成功；-1：修改群组信息失败
> 
> groupInfo：修改群组信息，json格式，定义如下：
> 
> - groupId：群组id，字符串类型；
> 
> - name：群组名称，字符串类型；

返回值：无

注：只有群组创建者才能成功调用该接口


<span id="ff_7">**inviteGroupMember(jsonData:Object,callbackFun:Function):void **</span>

<code>邀请成员加入</code>

参数：

jsonData：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选参数；
> 
> infos：需要添加用户信息，数组类型，数组元素为json格式，必选参数，定义如下：
> 
> - voipId：需要邀请的成员账号Id，字符串类型，必选项
> 
> - name：需要邀请的成员用户名，字符串类型，必选项

callFunction：群主邀请成员回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：邀请成员成功；-1：邀请成员失败
> 
> groupId：群组id，字符串类型；
> 
> infos：需要添加用户信息，数组类型，数组元素为json格式，定义如下：
> 
> - voipId：需要邀请的成员账号Id，字符串类型；
> 
> - name：需要邀请的成员用户名，字符串类型；

返回值：无

注：只有群组创建者才能成功调用该接口

<span id="ff_8">**deleteGroupMember(jsonData:Object,callbackFun:Function):void**</span>

<code>群主踢人/退出</code>

参数：

jsonData：传递参数，json格式，必选参数：

> groupId：群组id，字符串类型，必选项；
> 
> infos：需要踢出用户信息，数组类型，必选项，数组元素为json格式，定义如下：
> - voipId：需要踢出的成员账号Id，字符串类型，必选项；
> 
> - name：需要踢出的成员用户名，字符串类型，必选项；

callbackFun：群主踢人回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】。0：踢人成功；-1：踢人失败
> 
> groupId：群组id，字符串类型；
> 
> infos：需要踢出用户信息，数组类型，数组元素为json格式，定义如下：
> 
> - voipId：需要踢出的成员账号Id，字符串类型；
> 
> - name：需要踢出的成员用户名，字符串类型；


返回值：无


<span id="ff_9">**setGroupBlockStatus(jsonData:Object,callbackFun:Function):void **</span>

<code>设置自己在群组中屏蔽消息的设置</code>

参数：

jsonData：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选参数；
> 
> blockStatus：消息状态设置，必选参数，数字枚举型，【0，1，2】，0：接收消息并提醒；1：仅接收消息但不提醒；2：不接收消息

callFunction：设置自己在群组中屏蔽消息的设置回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：设置消息状态成功；-1：设置消息状态失败

返回值：无

<span id="ff_10">**getGroupInfo(jsonData:Object,callbackFun:Function):void **</span>

<code>获取群组消息</code>

参数：

jsonData：获取群组成员传递参数，json格式，定义如下：

> groupId：需查询群组id，字符串类型，必选参数；

callbackFun：查询群组成员回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：查询群组成功；-1：查询群组失败
> 
> groupId：群组id，字符串类型；
> 
> name：群组名称，字符串类型；
> 
> creator：群组创建人id，字符串类型；
> 
> voipIds：群组成员标识，字符串数组；
> 
> blockStatus：消息状态设置，整型数组，0：接收消息并提醒；1：仅接收消息但不提醒；2：不接收消息


返回值：无

<span id="ff_11">**groupExists(jsonData:Object,callbackFun:Function):void**</span>

<code> 检查群组是否存在</code>

参数：

jsonData：获取群组成员传递参数，json格式，定义如下：

> groupId：需查询群组id，字符串类型，必选参数；

callbackFun：查询群组是否存在回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1，-2】，0：群组存在；-1：群组不存在；-2：其他异常

返回值：无

<span id="ff_12">**getOwnGroup(callbackFun:Function):void**</span>

<code>获取用户所属群组</code>

参数：

callbackFun：获取登录后该用户所属群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】，0：查询群组成功；-1：查询群组失败
> groups：数组类型，数组元素为json格式，定义如下：
> 
> - groupId：群组id，字符串类型

返回值：无

注：该接口需在登录成功后调用方可生效

<span id="ff_13">**sendText(dataJson:Object,callFunction:Function):void **</span>

<code>单聊发送文本</code>

参数：

dataJson：单聊发送文本，json格式，定义如下：

> voipId：对方聊天人voipId，字符串类型，必选参数；
> 
> nickName：对方聊天人昵称，字符串类型，必选参数；
> 
> text：发送文本内容，字符串类型，必选项；

callFunction：发送回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。0：发送成功；其他值：发送失败；

返回值：无

注：该函数需要在Im登录成功后调用

<span id="ff_14">**sendImage(dataJson:Object,callFunction:Function)**</span>

<code>单聊发送图片</code>

参数：

dataJson：单聊发送图片，json格式，定义如下：
 
> voipId：对方聊天人voipId，字符串类型，必选参数；
> 
> nickName：对方聊天人昵称，字符串类型，必选参数；
> 
> imgPath：发送图片路径，字符串，支持sys:、res:、file:前缀，必选项；

callFunction：发送回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字；0：发送成功；其他值：发送失败


返回值：无

注：该函数需要在Im登录成功调用



<span id="ff_15">**sendGroupText(dataJson:Object,callFunction:Function):void **</span>

<code>群聊发送文本</code>

参数：

dataJson：群聊发送文本，json格式，定义如下：

> groupId：群组Id，字符串类型，必选参数；
> 
> text：发送文本内容，字符串，必选项；


callFunction：发送回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。0：发送成功；其他值：发送失败

返回值：无

注：该函数需要在Im登录成功后调用

<span id="ff_16">**sendGroupImage(dataJson:Object,callFunction:Function):void**</span>

<code>群聊发送图片</code>

参数：

dataJson：群聊发送文本，json格式，定义如下：

> groupId：群组Id，字符串类型，必选参数
> 
> imgPath：发送图片路径，字符串，支持sys:、res:、file:前缀，必选项

callFunction：发送回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。0：发送成功；其他值：发送失败；

返回值：无

注：该函数需要再Im登录成功后调用


