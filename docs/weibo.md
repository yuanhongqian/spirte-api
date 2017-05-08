# WeiBo 操作工具类

----------
微博WeiBo操作工具类，实现了用户信息获取，分享文本，分享图片，分享图文信息等功能。

使用时需要在js中引入 ：

```javascript
var weibo = require("WeiBo"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录： 

>**微博登录**
>
>[isWeiboInstalled(): boolean   新浪微博是否安装 ](#ff_0)
> 
> [login(jsonData:Object,callBackFun:Function): void  向新浪微博平台认证授权用户登录 ](#ff_1)
>
> [logout(callBackFun:Function): void    新浪微博用户登出 ](#ff_2)
>
> [getUserInfo(jsonData:Object,callBackFun:Function): void   获取已登录新浪微博用户基本信息 ](#ff_3)
>
>**微博分享**
>
> [shareText(jsonData:Object,callBackFun:Function): void   分享文本到新浪微博 ](#ff_4)
>
> [shareImage(jsonData:Object,callBackFun:Function): void   分享图片到新浪微博参数 ](#ff_5)
>
> [shareNews(jsonData:Object,callBackFun:Function): void  分享新闻（图文信息）到新浪微博 ](#ff_6)



<span id="ff_0">**isWeiboInstalled(): boolean**</span>  

<code>新浪微博是否安装</code>  

参数：无  

返回值：boolean型：  

> true：新浪微博已安装
> 
> false：新浪微博未安装



<span id="ff_1">**login(jsonData:Object,callBackFun:Function): void**</span>  

<code>向新浪微博平台认证授权用户登录</code> 

向新浪微博平台认证授权用户登录，获取token及uid值

参数：  

jsonData：Json对象，定义如下：  

> appKey：从新浪微博开放平台申请的 AppKey，字符串类型，可选项，若不设置则使用EDN打包配置值；  
> 
> redirectUrl：从新浪微博开放平台创建应用设置的回调页地址，字符串类型，可选项，若不设置则使用EDN打包配置值  

callbackFun：新浪微博用户授权认证回调，该函数具有json类型入参，入参定义如下： 

> code ：回应状态码，数字 
> 
> - 0：成功
> 
> - -1：失败
> 
> token：从新浪微博获取接口调用凭证，字符串
> 
> uid：从新浪微博获取授权用户唯一标识，字符串
> 
> expires：从新浪微博获取接口调用凭证token超时时间戳，距1970年1月1日午夜之间的毫秒数，数字

返回值：无






<span id="ff_2">**logout(callBackFun:Function): void**</span>  

<code>新浪微博用户登出</code> 

参数：
 
callbackFun：新浪微博用户授权认证回调，该函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字  
> 
> - 0：登出成功
> 
> - -1：登出失败



<span id="ff_3">**getUserInfo(jsonData:Object,callBackFun:Function): void**</span>  

<code>获取已登录新浪微博用户基本信息</code>   

获取已登录新浪微博用户基本信息，调用该函数前必须通过login函数获取

参数：
jsonData：Json对象，定义如下：  

> token：接口调用凭证，必选项，字符串
> 
> uid：从新浪微博获取授权用户唯一标识，必选项，字符串


callbackFun：新浪微博登录用户授权认证回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字,[0,-1]
> 
> - 0：获取用户信息成功
> 
> - -1：获取用户信息失败
> 
> id：int 用户UID
> 
> idStr：string	字符串型的用户UID
> 
> screenName：	string	用户昵称
> 
> name：string	友好显示名称
> 
> province：int	用户所在省级ID
> 
> city：int	用户所在城市ID
> 
> location：string	用户所在地
> 
> description：string	用户个人描述
> 
> url：string	用户博客地址
> 
> profileImageUrl：string	用户头像地址（中图），50×50像素
> 
> profileUrl：string	用户的微博统一URL地址
> 
> domain：string	用户的个性化域名
> 
> weihao：string	用户的微号
> 
> gender：string	性别，m：男、f：女、n：未知
> 
> followersCount：int	粉丝数
> 
> friendsCount：int	关注数
> 
> statusesCount：int	微博数
> 
> favouritesCount：int	收藏数
> 
> createdAt：string	用户创建（注册）时间
> 
> allowAllActMsg：boolean	是否允许所有人给我发私信，true：是，false：否
> 
> geoEnabled：boolean	是否允许标识用户的地理位置，true：是，false：否
> 
> verified：boolean	是否是微博认证用户，即加V用户，true：是，false：否
> 
> remark：string	用户备注信息，只有在查询用户关系时才返回此字段
> 
> allowAllComment：boolean	是否允许所有人对我的微博进行评论，true：是，false：否
> 
> avatarLarge：string	用户头像地址（大图），180×180像素
> 
> avatarHd：string	用户头像地址（高清），高清头像原图
> 
> verifiedReason：string	认证原因
> 
> followMe：boolean	该用户是否关注当前登录用户，true：是，false：否
> 
> onlineStatus：int	用户的在线状态，0：不在线、1：在线
> 
> biFollowersCount：int	用户的互粉数
> 
> lang：string	用户当前的语言版本，zh-cn：简体中文，zh-tw：繁体中文，en：英语




<span id="ff_4">**shareText(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享文本到新浪微博</code>

参数： 

jsonData：Json对象，定义如下：

text：发送的文本内容，字符串类型，必选项，不能为空且小于10K；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字 
> 
> -  0：分享成功 
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无


<span id="ff_5">**shareImage(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享图片到新浪微博参数</code>  

参数： 

jsonData：Json对象，定义如下：

imgPath：支持本地图片，必选项，本地图片路径，支持res: 及 file: 字符串；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字
> 
> -  0：分享成功
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无



<span id="ff_6">**shareNews(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享新闻（图文信息）到新浪微博</code>

参数：  

jsonData：Json对象，定义如下：

> url：要分享的新闻链接地址，必选项，字符串
> 
> title：要分享的新闻标题，必选项，字符串
> 
> description: 要分享的新闻内容，可选项，字符串
> 
> imgPath：要分享的新闻缩略图url，可选项，支持本地图片，必选项，本地图片路径，支持 res: 及 file: 字符串；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字 
> 
> -  0：分享成功 
>  
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无








