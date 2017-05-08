# Qq 操作工具类

----------
Qq 操作工具类，实现了qq登录，登出，获取登录用户信息，qq分享，qq空间分享等功能。

使用时需要在js中引入 ：

```javascript
var qq = require("Qq"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录： 

>**QQ登陆**
>
>[isQQInstalled(): boolean   QQ是否安装 ](#ff_0)
> 
> [login(jsonData:Object,callBackFun:Function): void  启动QQ进行登录用户授权认证 ](#ff_1)
> 
> [isLogin(): boolean    QQ用户是否已经登录](#ff_2)
>
> [logout(): void    登出QQ ](#ff_3)
>
> [getUserInfo(jsonData:Object,callBackFun:Function): void   获取授权QQ用户信息 ](#ff_4)
>
>**QQ分享**
>
> [shareImage(jsonData:Object,callBackFun:Function): void   分享图片到QQ好友 ](#ff_5)
>
> [shareNews(jsonData:Object,callBackFun:Function): void   分享新闻（图文信息）到QQ空间/QQ好友 ](#ff_6)
>
> [shareMusic(jsonData:Object,callBackFun:Function): void  分享音乐到QQ空间/QQ好友 ](#ff_7)





<span id="ff_0">**isQQInstalled(): boolean**</span>  

<code>QQ是否安装</code>  

参数：无  

返回值：boolean型：  

> true：QQ已安装
> 
> false：QQ未安装



<span id="ff_1">**login(jsonData:Object,callBackFun:Function): void**</span>  

<code>启动QQ进行登录用户授权认证</code> 

启动QQ进行登录用户授权认证，并返回授权结果

参数：   

jsonData：Json对象，定义如下：  

> scope：应用授权作用域，字符串枚举型，[get_user_info,all]，必选参数  
> 
> - get_user_info：获取用户个人信息权限，一般应用建议使用该作用域  
> 
> - all：获取所有权限；

callbackFun：QQ登录用户授权认证回调，该函数具有json类型入参，入参定义如下：  

> code ：回应状态码，数字,[0,-1]  
> 
> - 0：登录授权成功
> 
> - -1：登录授权失败
> 
> token：登录授权返回token，字符串类型,如：F2F085151E3B69E68EF9EFFF9C1D98A0
> 
> openId：登录授权返回openId，字符串类型，如：E483D6FAFB153162C2B26FD74DACEACC
> 
> expires：登录token的有效期，单位秒，字符串类型，如：7776000




<span id="ff_2">**isLogin(): boolean **</span>  

<code>QQ用户是否已经登录</code> 

参数：无

返回值：bool型

> true：当前QQ用户已登录
> 
> false：当前QQ用户未登录



<span id="ff_3">**logout(): void**</span>  

<code>登出QQ</code> 

参数：无

返回值：无





<span id="ff_4">**getUserInfo(jsonData:Object,callBackFun:Function): void**</span>  

<code>获取授权QQ用户信息</code>   

参数：
jsonData：Json对象，定义如下：

> token：登录授权返回token，字符串类型，必选项；
> 
> openId：登录授权返回openId，字符串类型，必选项；
> 
> expires：登录token的有效期，单位秒，字符串类型，必选项；

callbackFun：QQ登录用户授权认证回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字,[0,-1]
> 
> -   0：获取用户信息成功
> 
> -  -1：获取用户信息失败
> 
> city：用户所在城市，字符串
> 
> figureUrl：空间小头像（30px）网络url，字符串
> 
> figureUrl1：空间中头像（50px）网络url，字符串
> 
> figureUrl2：空间大头像（100px）网络url，字符串
> 
> figureurlQq1：用户小头像（40px）网络url，字符串
> 
> figureurlQq2 ：用户大头像（100px）网络url，字符串
> 
> gender：用户性别，字符串，男/女
> 
> level：用户账号级别，字符串
> 
> nickName：用户昵称，字符串
> 
> province：用户所在省份，字符串，如：江苏
> 
> isYellowVip：是否为黄钻用户，，字符串，0非黄钻，1黄钻
> 
> yellowVipLevel：用户账户黄钻等级，字符串

**注：** 获取用户信息，需在qq单点登录成功后方可调用





<span id="ff_5">**shareImage(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享图片到QQ好友</code>  

参数： 
jsonData：Json对象，定义如下：

> imgPath：只支持本地图片，必选项，本地图片路径，支持res: 及 file: 字符串；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字  
> 
> - 0：分享成功  
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无


<span id="ff_6">**shareNews(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享新闻（图文信息）到QQ空间/QQ好友</code>

参数：  

jsonData：Json对象，定义如下：

> type：字符串枚举型,[QFriend，QZone]，可选项，默认QZone
> 
> - QZone：qq空间（默认）
> 
> - QFriend：qq好友
> 
> url：要分享的新闻链接地址，必选项，字符串,仅支持网络地址
> 
> title：要分享的新闻标题，必选项，字符串
> 
> description: 要分享的新闻内容，可选项，字符串
> 
> imgPath：要分享的新闻缩略图url，可选项，支持本地及网络图片；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> -  0：分享成功
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无




<span id="ff_7">**shareMusic(jsonData:Object,callBackFun:Function): void**</span>  

<code>分享音乐到QQ空间/QQ好友</code>

参数：  

jsonData：Json对象，定义如下：

> type：字符串枚举型,[QFriend，QZone]，可选项，默认QZone 
> 
> - QZone：qq空间（默认）
> 
> - QFriend：qq好友
> 
> url：要分享的音乐链接地址，必选项，字符串，必选项
> 
> title：要分享的音乐名，必选项，字符串
> 
> description: 要分享的音乐描述，可选项，字符串
> 
> imgPath：要分享的音乐缩略图url，可选项，支持本地及网络图片；

callbackFun：分享回调，该函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字
> 
> - 0：分享成功
> 
> - 其他值：分享失败
> 
> errMsg：错误消息描述，字符串类型，当errCode为非0时有效

返回值：无

**注：** 音乐分享后，发送方和接收方在聊天窗口中点击消息气泡即可开始播放音乐。







