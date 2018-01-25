# Mplus组件


------------------


Mplus组件用于处理同Mplus平台交互。

Mplus为外置组件。

<h2 id="cid_1">方法</h2>

本节目录：

> [invoke(dataJson:Object,callFunction:Function):void 调用Mplus相关接口](#ff_0)

<span id="ff_0">**invoke(dataJson:Object,callFunction:Function):void**</span>

<code>调用Mplus相关接口</code>

参数：

dataJson：调用传递参数，json格式，必选项，目前支持：通讯录选人，云盘文件选择两种传参调用，定义如下：

> **【通讯录选人】**
> 
> method：调用方法名，固定位selectMembersFromContact，字符串类型；
> 
> param：调用传递参数，json格式，定义如下：
> 
> - showType：通讯录展示类型，数字枚举型，【0，1】，0：默认界面；1：默认邮箱
> 
> **【云盘文件选择】**
> 
> method：调用方法名，固定为selectDocsFromCloudDisk，字符串类型；
> 
> param：调用传递参数，json格式，空json；

callFunction：回调函数，入参json格式，定义如下：

> **【通讯录选人】**
> 
> status：状态码，数字枚举型，【0，-1】，0：成功；-1：失败
> 
> errMsg：失败原因，字符串枚举型
> 
> param：json数组类型，json格式定义如下：
> 
> - memberId：成员id，字符串类型；
> 
> - loginId：字符串类型；
> 
> - name：昵称，字符串类型；
> 
> - mail：默认邮箱，字符串类型；
> 
> - jianpin：姓名简拼，字符串类型；
> 
> - photoUrl：头像url，若为空则不存在；
> 
> **云盘文件选择**
> 
> status：状态码，数字枚举型，【0，-1】，0：成功；-1：失败
> 
> errMsg：失败原因，字符串枚举型
> 
> param：json数组类型，定义如下：
> 
> - id：文件id，字符串类型
> 
> - name：文件名，字符串类型
> 
> - preview：预览模式，数字枚举型，【0，1】，0：无法预览；1：可以预览；
> 
> - downloadFlag：下载模式，数字枚举型，【0，1】，0：禁止下载；1：允许下载；
> 
> createtime：文件创建时间，字符串类型；
> 
> size：文件大小，数字类型，单位K
> 
> documentDesc：文件摘要，字符串类型；
> 
> documentCreater：文件上传用户，字符串类型

返回值：无

