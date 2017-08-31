# RlyIm功能组件

----------
容联云Im可以快速实现公有云IM通信功能，支持单聊，群聊，消息通知等。  

Sprite集成容联云IM功能，将单聊，群聊，消息通知，群组通知以UI组件方式提供，同时提供相关工具类组件实现登录，注销等功能。


RlyIm 为容联云IM工具类，提供登录，注销等相关操作方法，外置组件。

使用时需要在js中引入 ：

```javascript
var rlyIm = require("RlyIm"); 
```

**注：** 该组件为外置功能组件，打包需要选择。


<h2 id="cid_1">js方法</h2>  


本节目录：

[login (loginDataJson:Object,onLoginFunction:Function):void   启动容联云IM初始化并进行用户登录](#ff_0)

[refreshImData(rereshFunction:Function):void   刷新Im用户信息数据](#ff_1)

[logout():void   注销当前已登录IM用户](#ff_2)

[setSettingInfo(settingInfoJson:Object):void  设置容联云IM 服务器设置信息](#ff_3)  

[createGroup (dataJson:Object,callFunction:Function):void  创建群组 ](#ff_4)

[getGroupMembes(dataJson:Object,callFunction:Function):void  获取群组内所有成员信息](#ff_5)

[searchGroupById(dataJson:Object,callFunction:Function):void  根据群组Id搜索群组](#ff_6)

[searchGroupByName(dataJson:Object,callFunction:Function) :void  根据群组名称搜索群组](#ff_7)

[getOwnGroup(callFunction:Function):void  获取用户所属群组](#ff_8)

[quitGroup(dataJson:Object,callFunction:Function):void  退出指定群组](#ff_9)

[joinGroup(dataJson:Object,callFunction:Function):void  加入指定群组   ](#ff_10)

[deleteGroupMember(dataJson:Object,callFunction:Function):void  群主踢人 ](#ff_11)

[forbidGroupMember(dataJson:Object,callFunction:Function):void  群组禁言](#ff_12)

[allowGroupMember(dataJson:Object,callFunction:Function):void  群组关闭禁言](#ff_13)

[inviteGroupMember(dataJson:Object,callFunction:Function):void  邀请成员加入](#ff_14)

[modifyGroup(dataJson:Object,callFunction:Function):void  修改群组信息](#ff_15)

[deleteGroup (dataJson:Object,callFunction:Function):void  解散群组](#ff_16)

[setGroupRule(dataJson:Object,callFunction:Function):void  设置群组规则](#ff_17)

[setPersonInfo(dataJson:Object,callFunction:Function):void  设置登录用户个人信息，包括昵称、生日、性别等](#ff_18)

[getPersonInfo(callFunction:Function):void  获取登录用户个人信息，包括昵称、生日、性别等](#ff_19)

[getSettingInfo():Object  获取容联云IM 服务器设置信息 ](#ff_20) 

[getGroupInfo(dataJson:Object,callFunction:Function):void  获取群组信息 ](#ff_21)

[getGroupMember(dataJson:Object,callFunction:Function):void  获取群组指定成员  ](#ff_22)

[getGroupMembers(dataJson:Object,callFunction:Function):void  获取群组内所有成员信息 ](#ff_23)

[getUnreadMessageNumber():Object  获取未读消息条数  ](#ff_24)

[void sendText(dataJson，callFunction)  单聊发送文本](#ff_25)

[sendImage(dataJson: Object, callFunction: Function): void   单聊发送图片](#ff_26)

[sendGroupText(dataJson: Object, callFunction: Function): void   群聊发送文本](#ff_27)

[sendGroupImage(dataJson: Object, callFunction: Function): void   群聊发送图片](#ff_28)



<span id="ff_0">**login (loginDataJson:Object,onLoginFunction:Function):void**</span>  

<code>启动容联云IM初始化并进行用户登录</code>  

启动容联云IM初始化并进行用户登录，处理结果进入回调中返回

注： 容联云后面所有的功能都必须在成功登录后才能使用。

参数：  

loginDataJson：登录用户传递数据，json格式，定义如下：  

> type：登录模式,数字，[0,1]，必选项
> 
> - 0：容联云Voip账号模式 
> 
> - 1：第三方账号模式
> 
> 【容联云Voip账号】模式定义：
> 
> appId：应用appid，必选项；
> 
> appToken：应用apptoken，必选项
> 
> userId：容联云子账号voipId，必选项；
> 
> password:容联云子账号voip密码，必选项；
> 
> 
> 【第三方账号模式】模式定义： 
> 
> appId：应用appid，必选项； 
> 
> appToken：应用appToken，必选项；
> 
> userId：第三方应用系统账号，调用登录接口后容联云服务器会自注册，后续启动聊天时改值可视为voipId，需保证唯一，必选项； 
> 
>** 注：**  
>
> - 容联云第三方账号里面不能以g开头，里面也不能含有@符号。
> 
> -  sprite中默认是强登录模式，如果在另外一台设备登录，会挤掉之前设备登录的用户，不过和网页版用户登录不冲突。


onLoginFunction：登录回调函数，该回调函数具有一个入参，类型为数字： 

> code：数字
> 
> -  0：登录容联云IM服务器成功，
> 
> -  其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box

返回值：无

**注：** 关于容联云两种登录模式详细说明见：http://www.yuntongxun.com/api/im/readyJob#point_box



<span id="ff_1">**refreshImData(rereshFunction: Function): void**</span>  

<code>刷新Im用户信息数据</code>   

参数： 
 
rereshFunction：获取Im关联数据回调函数，该回调函数具有一个入参，类型为数字： 

> code：数字
> 
> - 0：获取数据成功
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box

**注：** 该函数需要在Im登录成功后调用

<span id="ff_2">**logout():void**</span>  

<code>注销当前已登录IM用户</code>  

参数：无 

返回值：无


<span id="ff_3">**setSettingInfo(settingInfoJson: Object): void**</span>  

<code>设置容联云IM服务器设置信息</code>  

参数：Json格式，定义如下： 

> ip：im服务器地址，字符串
> 
> port：im服务器端口，数字
> 
> iconUrl：im头像图片请求url地址，字符串；
> 
> dataUrl：im联系人信息请求url地址，字符串；
> 
> vibrate：新消息是否震动 bool型
> 
> - true：震动（默认）
> 
> - false：不震动
> 
> sound：新消息是否播放声音 bool型
> 
> - true：播放提示音（默认）
> 
> - false：不播放提示音

返回值：无 



<span id="ff_4">** createGroup(dataJson: Object, callFunction: Function): void**</span>  

<code>创建群组</code>  

参数： 

dataJson：登录用户传递数据，json格式，定义如下：

> name：设置群组名称，字符串类型，必选参数；
> 
> declare：设置群组公告，字符串类型，可选参数；
> 
> permission：设置群组验证权限，数字枚举型，【1, 2,3】,可选项，默认不验证权限；
> 
> - 1: 不需要身份验证（默认）
> 
> - 2: 需要群组创建人身份验证
> 
> - 3: 私有群组
> 
> isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
> - 0：标准群组（默认）
> 
> - 1：讨论组
>  
> scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
> - 1：临时组，上限100人
> 
> - 2：普通组，上限300人（默认）
> 
> - 3：普通高级组，上限500人
> 
> - 4：VIP组，上限1000人
> 
> - 5：高级VIP组，上限2000人

callFunction：创建群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> - 0：创建群组成功
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
>
> groupInfo: 创建群组信息，json格式，定义如下：
> 
> -   groupId：群组id，字符串类型
> 
> -   name：群组名称，字符串类型；
> 
> -   declare：设置群组公告，字符串类型；
> 
> -   permission：设置群组验证权限，数字枚举型，【1, 2,3】,可选项，默认不验证权限；
> 
>  -   1: 不需要身份验证（默认）
>  
>  -   2: 需要群组创建人身份验证
>  
>  -   3: 私有群组
>
> - isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
>  - 0：标准群组（默认）
> 
>  - 1：讨论组
>
> - scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
>  - 1：临时组，上限100人
> 
>  - 2：普通组，上限300人（默认）
> 
>  - 3：普通高级组，上限500人
> 
>  - 4：VIP组，上限1000人
> 
>  - 5：高级VIP组，上限2000人

返回值：无  

**注：** 容联云基础版只能创建临时组100人，并且一次只能邀请5个人建组。


<span id="ff_5">**getGroupMembes(dataJson: Object, callFunction: Function): void**</span>  

<code>获取群组内所有成员信息</code>  

参数： 

dataJson：获取群组成员传递参数，json格式，定义如下：

> groupId：需查询群组id，字符串类型，必选参数；

callFunction：查询群组成员回调函数，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字,[0,-1]
> 
> -   0：获取群组成员成功
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> members: 数组类型，数组元素为json格式，定义如下：
> 
> -   voipId：成员子voip账号id，字符串类型；
> 
> -   displayName：，成员显示名，字符串类型；
> 
> -   tel：电话，字符串类型；
> 
> -   email：邮件，字符串类型；
> 
> -   remark：备注，字符串类型；
> 
> -   sex：性别，数字，【1,2】
> 
>  -     1：男
>  
>  -     2：女
>  
> -   owner：普通成员还是群组管理员，数字，【1,2,3】
> 
>   -      1：创建者
>   
>   -      2：管理员
>   
>   -      3：普通成员
> 
> -   ban：成员是否被禁言，数字，【1,2】
> 
>  -      1：普通状态
>  
>  -      2：禁言状态


返回值：无  


<span id="ff_6">**searchGroupById(dataJson: Object, callFunction: Function): void**</span>  

<code>根据群组Id搜索群组</code>   

参数： 

dataJson：获取群组成员传递参数，json格式，定义如下：
> 
> id：需查询群组id，字符串类型，必选参数；

callFunction：查询群组成员回调函数，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字,[0,-1]
> 
> -   0：查询群组成功
> -   
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groups: 数组类型，数组元素为json格式，定义如下：
> 
> -   groupId：群组id，字符串类型
> 
> -   name：群组名称，字符串类型；
> 
> -   declare：设置群组公告，字符串类型；
> 
> -   permission：群组验证权限，数字枚举型，【1, 2,3】,默认不验证权限；
> 
>  -    1: 不需要身份验证（默认）
>  
>  -    2: 需要群组创建人身份验证
>  
>  -    3: 私有群组
>  
> -  silence：群组是否免打扰，数字，【0,1】，可选项；
> 
>  -    0：不设置群组免打扰（默认）
>  
>  -    1：设置群组免打扰
>  
> - isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
>  -    0：标准群组（默认）
>  
>  -    1：讨论组
>   
> - scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
>  -    1：临时组，上限100人
> 
>  -    2：普通组，上限300人（默认）
> 
>  -    3：普通高级组，上限500人
> 
>  -    4：VIP组，上限1000人
> 
>  -    5：高级VIP组，上限2000人 


返回值：无


<span id="ff_7">**searchGroupByName(dataJson: Object, callFunction: Function): void**</span>  

<code>根据群组名称搜索群组</code>   

参数： 

dataJson：获取群组成员传递参数，json格式，定义如下：
> 
> name：需查询群组名称，字符串类型，必选参数；

callFunction：查询群组成员回调函数，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字,[0,-1]
> 
> -   0：查询群组成功
> 
> - 其他值：登录容联云IM服务器失败， 错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groups: 数组类型，数组元素为json格式，定义如下：
> 
> -   groupId：群组id，字符串类型
> 
> -   name：群组名称，字符串类型；
> 
> -   declare：设置群组公告，字符串类型；
> 
> -   permission：群组验证权限，数字枚举型，【1, 2,3】,默认不验证权限；
> 
>  -    1: 不需要身份验证（默认）
>  
>  -    2: 需要群组创建人身份验证
>  
>  -    3: 私有群组
>  
> -  silence：群组是否免打扰，数字，【0,1】，可选项；
> 
>  -    0：不设置群组免打扰（默认）
>  
>  -    1：设置群组免打扰
>  
> - isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
>  -    0：标准群组（默认）
>  
>  -    1：讨论组
> 
> - scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
>  -    1：临时组，上限100人
>  
>  -    2：普通组，上限300人（默认）
>  
>  -    3：普通高级组，上限500人
>  
>  -    4：VIP组，上限1000人
>  
>  -    5：高级VIP组，上限2000人

返回值：无 

**注：**  群组名必须完全一致，不支持模糊匹配。

<span id="ff_8">** getOwnGroup(callFunction: Function): void**</span>  

<code>获取用户所属群组</code>  

参数：

callFunction：获取登录后该用户所属群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：查询群组成功
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groups: 数组类型，数组元素为json格式，定义如下：
> 
> - groupId：群组id，字符串类型
> 
> - name：群组名称，字符串类型；
> 
> - declare：设置群组公告，字符串类型；
> 
> - permission：群组验证权限，数字枚举型，【1, 2,3】,默认不验证权限；
> 
>  - 1: 不需要身份验证（默认）
> 
>  - 2: 需要群组创建人身份验证
> 
>  - 3: 私有群组
> 
> - silence：群组是否免打扰，数字，【0,1】，可选项；
> 
>  - 0：不设置群组免打扰（默认）
> 
>  - 1：设置群组免打扰
> 
> - isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
>  - 0：标准群组（默认）
> 
>  - 1：讨论组
>  
> - scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
>  - 1：临时组，上限100人
> 
>  - 2：普通组，上限300人（默认）
> 
>  - 3：普通高级组，上限500人
> 
>  - 4：VIP组，上限1000人
> 
>  - 5：高级VIP组，上限2000人

返回值：无

**注：** 该接口需在登录成功后调用方可生效




<span id="ff_9">**quitGroup(dataJson: Object, callFunction: Function): void**</span>  

<code>退出指定群组</code> 

参数： 

dataJson：获取群组成员传递参数，json格式，定义如下：

> groupId：需查询群组id，字符串类型，必选参数；

callFunction：退出群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：退出群组成功
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupId：退出群组id，字符串类型

返回值：无  


<span id="ff_10">**joinGroup(dataJson: Object, callFunction: Function): void**</span>  

<code>加入指定群组</code>

参数： 

dataJson：加入群组传递参数，json格式，定义如下：

> groupId：需要加入群组id，字符串类型，必选参数；
> 
> declare：加入群组理由，字符串类型，可选参数；

callFunction：加入群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：加入群组成功，若该群组不需要身份认证，则加入成功，若该群组需要身份认证，则需等待审核；
> - 其他值：登录容联云IM服务器失败， 错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupId：加入群组id，字符串类型

返回值：无  

<span id="ff_11">**deleteGroupMember(dataJson: Object, callFunction: Function): void**</span>  

<code>群主踢人</code>

参数： 

dataJson：传递参数，json格式，定义如下：
> 
> groupId：群组id，字符串类型，必选参数；
> 
> voipId：需要踢出成员id，字符串类型，必选参数；


callFunction：群主踢人回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：踢人成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupId：群组id，字符串类型
> 
> voipId：踢出成员id，字符串类型；

返回值：无

**注：** 只有群组创建者才能成功调用该接口 

 
<span id="ff_12">**forbidGroupMember(dataJson: Object, callFunction: Function): void**</span>  

<code>群组禁言</code> 

参数：

dataJson：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选参数；
> 
> voipId：需要禁言成员id，字符串类型，必选参数；


callFunction：群主禁言回调函数，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字,[0,-1]
> 
> -   0：禁言成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupId：群组id，字符串类型
> 
> voipId：禁言成员id，字符串类型；

返回值：无

**注：** 只有群组创建者才能成功调用该接口  


<span id="ff_13">** allowGroupMember(dataJson: Object, callFunction: Function): void**</span>  

<code>群组关闭禁言</code> 

参数： 

dataJson：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选参数；
> 
> voipId：需要关闭禁言成员id，字符串类型，必选参数；


callFunction：群主关闭禁言回调函数，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字,[0,-1]
> 
> -   0：关闭禁言成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupId：群组id，字符串类型
> 
> voipId：关闭禁言成员id，字符串类型；

返回值：无

**注：** 只有群组创建者才能成功调用该接口  

<span id="ff_14">**inviteGroupMember(dataJson: Object, callFunction: Function): void**</span>  

<code>邀请成员加入</code> 

参数：
dataJson：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选参数；
> 
> reason：邀请原因，字符串类型，可选参数；
> 
> confirm：是否需要对方确认，数字，[1,2]，可选项
> 
> -    1：不需要对方确认（默认）
> 
> -    2：需要对方确认
> 
> voipIds：需要邀请的成员，数组类型，数组元素为字符串，必选参数；


callFunction：群主邀请成员回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：邀请成员成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupId：群组id，字符串类型
> 
> voipIds：需要邀请的成员，数组类型，数组元素为字符串，必选参数；

返回值：无

注：只有群组创建者才能成功调用该接口


<span id="ff_15">**modifyGroup(dataJson: Object, callFunction: Function): void**</span>  

<code>修改群组信息</code> 

参数： 

dataJson：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选参数；
> 
> name：设置群组名称，字符串类型，可选参数；
> 
> declare：设置群组公告，字符串类型，可选参数；
> 
> permission：设置群组验证权限，数字枚举型，【1, 2,3】,可选项，默认不验证权限；
> 
> -    1: 不需要身份验证（默认）
> 
> -    2: 需要群组创建人身份验证
> 
> -    3: 私有群组
> 
> isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
> -    0：标准群组（默认）
> 
> -    1：讨论组
>  
> scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
> -    1：临时组，上限100人
> 
> -    2：普通组，上限300人（默认）
> 
> -    3：普通高级组，上限500人
> 
> -    4：VIP组，上限1000人
> 
> -    5：高级VIP组，上限2000人

callFunction：修改群组信息回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：修改群组信息成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
>  
> groupInfo: 修改群组信息，json格式，定义如下：
> 
> -   groupId：群组id，字符串类型
> 
> -   name：群组名称，字符串类型；
> 
> -   declare：设置群组公告，字符串类型；
> 
> -   permission：群组验证权限，数字枚举型，【1, 2,3】，默认不验证权限；
> 
>  -    1: 不需要身份验证（默认）
> 
>  -    2: 需要群组创建人身份验证
> 
>  -    3: 私有群组
> 
> -   silence：群组是否免打扰，数字，【0,1】，必选项；
> 
>  -    0：不设置群组免打扰
> 
>  -    1：设置群组免打扰
> 
>  -   isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
>  -    0：标准群组（默认）
> 
>  -    1：讨论组
>  
> -   scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
>  -    1：临时组，上限100人
> 
>  -    2：普通组，上限300人（默认）
> 
>  -    3：普通高级组，上限500人
> 
>  -    4：VIP组，上限1000人
> 
>  -    5：高级VIP组，上限2000人

返回值：无

**注：** 只有群组创建者才能成功调用该接口


<span id="ff_16">**deleteGroup(dataJson: Object, callFunction: Function): void**</span>  

<code>解散群组</code>  

参数： 

dataJson：传递参数，json格式，定义如下：
> 
> groupId：群组id，字符串类型，必选参数；
> 
> callFunction：解散群组回调函数，该函数具有json类型入参，入参定义如下： 
> 
> code：回应状态码，数字,[0,-1]
> 
> -   0：解散群组成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupId：群组id，字符串类型

返回值：无

**注：** 只有群组创建者才能成功调用该接口


<span id="ff_17">**setGroupRule(dataJson: Object, callFunction: Function): void**</span>  

<code>设置群组规则</code>  

参数：

dataJson：传递参数，json格式，定义如下：

> groupId：群组id，字符串类型，必选参数；
> 
> silence：设置群组是否免打扰，数字，【0,1】，必选项；
> 
> -    0：不设置群组免打扰
> 
> -    1：设置群组免打扰

callFunction：设置群组规则，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：设置群组规则成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 

> groupId：群组id，字符串类型

返回值：无

**注：** 群组免打扰功能是指群组收到消息的时候，是否震动手机或振铃（震动或振铃是在应用层处理，
通过sdk可以设置此状态并保存在服务端，切换手机时，群组的状态也可同步


<span id="ff_18">**setPersonInfo(dataJson: Object, callFunction: Function): void**</span>  

<code>设置登录用户个人信息，包括昵称、生日、性别等</code>  

参数：

dataJson：传递参数，json格式，定义如下：

> nickName：设置昵称，字符串类型，必选参数；
> 
> sex：设置性别，数字，【1,2】，可选参数，默认男
> 
> -     1：男
> 
> -     2：女
> 
> birth：设置生日，格式：2015-5-13，字符串类型，可选参数；

callFunction：设置个人信息回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：设置个人信息成功 
> 
> - 其他值：登录容联云IM服务器失败，错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box

返回值：无

**注：** 登录成功后方可调用该接口 


<span id="ff_19">** getPersonInfo(callFunction: Function): void**</span>  

<code>获取登录用户个人信息，包括昵称、生日、性别等</code>

参数：
callFunction：获取登录个人信息回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：设置个人信息成功 
> 
> - 其他值：登录容联云IM服务器失败, 错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> 
> personInfo: 用户个人信息，json格式，定义如下：
> 
> voipId：当前用户voipId，字符串类型；
> 
> nickName：设置昵称，字符串类型；
> 
> sex：设置性别，数字，【1,2】，默认男
> 
> -     1：男
> 
> -     2：女
> 
> birth：设置生日，格式：2015-5-13，字符串类型；

返回值：无

**注：** 登录成功后方可调用该接口  


<span id="ff_20">** getSettingInfo(): Object**</span>  

<code>获取容联云IM服务器设置信息</code>

参数：无

返回值：Json格式，定义如下：

> ip：im服务器地址，字符串
> 
> port：im服务器端口，数字
> 
> iconUrl：im头像图片请求url地址，字符串；
> 
> vibrate：新消息是否震动 bool型
> 
> - true：震动
> 
> - false：不震动
> 
> sound：新消息是否播放声音 bool型
> 
> - true：播放提示音
> 
> - false：不播放提示音


<span id="ff_21">**getGroupInfo(dataJson: Object, callFunction: Function): void**</span>  

<code>获取群组信息</code>

参数：

dataJson：获取群组成员传递参数，json格式，定义如下：

> groupId：需查询群组id，字符串类型，必选参数；

callFunction：获取群组信息回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：获取群组信息成功
> 
> - 其他值：登录容联云IM服务器失败, 错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> groupInfo: 创建群组信息，json格式，定义如下：
> 
> -   groupId：群组id，字符串类型
> 
> -   name：群组名称，字符串类型；
> 
> -   declare：设置群组公告，字符串类型；
> 
> -   permission：群组验证权限，数字枚举型，【1, 2,3】,默认不验证权限；
> 
>  -    1: 不需要身份验证（默认）
>  
>  -    2: 需要群组创建人身份验证
>  
>  -    3: 私有群组
>  
> -  silence：群组是否免打扰，数字，【0,1】；
> 
>  -    0：不设置群组免打扰（默认）
>  
>  -    1：设置群组免打扰
>  
> - isDiscuss：是否创建讨论组，可选项，【0,1】默认为0标准群组
> 
>  -    0：标准群组（默认）
>  
>  -    1：讨论组
> -  
> - scope：设置群组类型，数字枚举型，【1,2,3,4,5】
> 
>  -    1：临时组，上限100人
>  
>  -    2：普通组，上限300人（默认）
>  
>  -    3：普通高级组，上限500人
>  
>  -    4：VIP组，上限1000人
>  
>  -    5：高级VIP组，上限2000人

返回值：无


<span id="ff_22">**getGroupMember(dataJson: Object, callFunction: Function): void**</span>  

<code>获取群组指定成员</code>

参数：
dataJson：获取群组成员传递参数，json格式，定义如下：

> groupId：需查询群组id，字符串类型，必选参数；
> 
> voipId：需查询成员子voip账号id，字符串类型，必选参数；

callFunction：查询群组成员回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字,[0,-1]
> 
> -   0：获取群组成员成功
> 
> - 其他值：登录容联云IM服务器失败, 错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
>
> member: 成员信息，json格式： 
>
> - voipId：成员子voip账号id，字符串类型；
> 
> - displayName：，成员显示名，字符串类型；
> 
> - tel：电话，字符串类型；
> 
> - email：邮件，字符串类型；
> 
> - remark：备注，字符串类型；
> 
> - sex：性别，数字，【1,2】
> 
>  - 1：男
> 
>  - 2：女
> 
> - owner：普通成员还是群组管理员，数字，【1,2,3】
> 
>  -  1：创建者
> 
>  -  2：管理员
> 
>  -  3：普通成员
> 
> - ban：成员是否被禁言，数字，【1,2】
> 
>  -  1：普通状态
> 
>  -  2：禁言状态

返回值：无


<span id="ff_23">**getGroupMembers(dataJson: Object, callFunction: Function): void**</span>  

<code>获取群组内所有成员信息</code> 

参数： 

dataJson：获取群组成员传递参数，json格式，定义如下：

> groupId：需查询群组id，字符串类型，必选参数；

callFunction：查询群组成员回调函数，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字,[0,-1]
> 
> -   0：获取群组成员成功
> 
> - 其他值：登录容联云IM服务器失败,错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box
> 
> members: 成员信息数组，成员为json格式，定义如下：
> 
> -   voipId：成员子voip账号id，字符串类型；
> 
> -   displayName：，成员显示名，字符串类型；
> 
> -   tel：电话，字符串类型；
> 
> -   email：邮件，字符串类型；
> 
> -   remark：备注，字符串类型；
> 
> -   sex：性别，数字，【1,2】
> 
>  -     1：男
> 
>  -     2：女
> 
> -   owner：普通成员还是群组管理员，数字，【1,2,3】
> 
>  -      1：创建者
> 
>  -      2：管理员
> 
>  -      3：普通成员
> 
> -   ban：成员是否被禁言，数字，【1,2】
> 
>  -      1：普通状态
> 
>  -      2：禁言状态

返回值：无  


<span id="ff_24">**getUnreadMessageNumber(): Object**</span>  

<code>获取未读消息条数</code> 

参数：无

返回值：Json类型，定义如下：

> total：未读消息总数，包括单聊，群聊，系统通知
> 
> member：单聊未读消息数
> 
> group：群聊未读消息数
> 
> system：系统通知未读消息数；


<span id="ff_25">** sendText(dataJson: Object, callFunction: Function): void**</span>  

<code>单聊发送文本</code> 

参数： 

dataJson：单聊发送文本，Json格式，定义如下： 

> voipId：对方聊天人voipId，字符串类型，必选参数
> 
> nickName：对方聊天人昵称，字符串类型，必选参数；
> 
> text：发送文本内容，字符串，必选项；

callFunction：发送回调函数，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字。
> 
> - 0：发送成功；
> 
> - 其他值：发送失败, 错误码参见容联云错误码说明： http://www.yuntongxun.com/api/im/im_1_3#point_box

返回值：无 


**注： ** 该函数需要在Im登录成功后调用 


<span id="ff_26">**sendImage(dataJson: Object, callFunction: Function): void;**</span>  

<code>单聊发送图片</code> 

参数：

dataJson：单聊发送文本，Json格式，定义如下：

> voipId：对方聊天人voipId，字符串类型，必选参数；
> 
> nickName：对方聊天人昵称，字符串类型，必选参数；
> 
> imgPath：发送图片路径，字符串，支持sys: res: file: 前缀，必选项；

callFunction：发送回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。
> 
> - 0：发送成功；
> 
> - 其他值：发送失败,错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box

返回值：无

**注：** 该函数需要在Im登录成功后调用 


<span id="ff_27">**sendGroupText(dataJson: Object, callFunction: Function): void**</span>  

<code>群聊发送文本</code>

参数：
dataJson：群聊发送文本，Json格式，定义如下：

> groupId：群组Id，字符串类型，必选参数
> 
> text：发送文本内容，字符串，必选项；

callFunction：发送回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。
> 
> - 0：发送成功；
> 
> - 其他值：发送失败, 错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box

返回值：无

**注：** 该函数需要在Im登录成功后调用


<span id="ff_28">**sendGroupImage(dataJson: Object, callFunction: Function): void**</span>  

<code>群聊发送图片</code>

参数：

dataJson：群聊发送文本，Json格式，定义如下：

> groupId：群组Id，字符串类型，必选参数
> 
> imgPath：发送图片路径，字符串，支持sys: res: file: 前缀，必选项；

callFunction：发送回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。
> 
> - 0：发送成功；
> 
> - 其他值：发送失败,错误码参见容联云错误码说明：http://www.yuntongxun.com/api/im/im_1_3#point_box

返回值：无

**注：** 该函数需要在Im登录成功后调用
