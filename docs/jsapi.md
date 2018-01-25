# js功能组件概述


----------

Sprite采用CommonJS规范，通过require("模块标识")来实现对系统api对象引用，如使用Device对象方法。

```javascript
     var device = require("Device"); 
     var version = device.getVersion();
```


<h2 id="cid_1">js组件类别</h2>   

**基础类**  

> [App：应用信息获取类](https://gitdocument.exmobi.cn/sprite-api/app.html)
> 
> [Window：页面操作相关类](https://gitdocument.exmobi.cn/sprite-api/window.html)
> 
> [Document：页面Dom操作类](https://gitdocument.exmobi.cn/sprite-api/document.html)
> 
> [Device：设备信息获取类](https://gitdocument.exmobi.cn/sprite-api/device.html)
> 
> [Native：原生程序相关操作类](https://gitdocument.exmobi.cn/sprite-api/native.html)
> 
> [Encryption：编/解码工具类](https://gitdocument.exmobi.cn/sprite-api/encryption.html)
> 
> [Time：定时器类](https://gitdocument.exmobi.cn/sprite-api/time.html)


**数据存储**  

> [File：文件操作类](https://gitdocument.exmobi.cn/sprite-api/file.html)
> 
> [Db：数据库操作类](https://gitdocument.exmobi.cn/sprite-api/db.html)
> 
> [DbCipher：加密数据库操作类](https://gitdocument.exmobi.cn/sprite-api/dbcipher.html)
> 
> [MemCache：内存缓存存取类](https://gitdocument.exmobi.cn/sprite-api/memcache.html)
> 
> [DiskCache：磁盘缓存存取类](https://gitdocument.exmobi.cn/sprite-api/diskcache.html)
> 
> [Clipboard：系统剪切板类](https://gitdocument.exmobi.cn/sprite-api/clipboard.html)

**日程通知**

> [Agenda：日程操作类](https://gitdocument.exmobi.cn/sprite-api/agenda.html)
> 
> [LocalNotification：本地通知类](https://gitdocument.exmobi.cn/sprite-api/localnotification.html)

**网络相关**  

> [Http：Http网络操作类](https://gitdocument.exmobi.cn/sprite-api/http.html)
> 
> [WebSocket：WebSocket网络操作类](https://gitdocument.exmobi.cn/sprite-api/websocket.html)
> 
> [NetInfo：网络信息相关类](https://gitdocument.exmobi.cn/sprite-api/netinfo.html)


**界面相关**   

> [UI：界面相关操作类](https://gitdocument.exmobi.cn/sprite-api/ui.html) 包括：alert，toast，confirm，selectFile，selectImage，selectTime，selectDate等

**多媒体**  

> Audio：音频操作相关类
> 
> - 包括：[AudioRecord录音操作类](https://gitdocument.exmobi.cn/sprite-api/audiorecord.html)，[AudioPlay音频播放类](https://gitdocument.exmobi.cn/sprite-api/audioplay.html)， 
> 
> [VideoUtil：视频操作相关类](https://gitdocument.exmobi.cn/sprite-api/videoutil.html)
> 
> - 包括：recordShortVideo小视频录制，openVideo视频播放等

**扫描拍照**  

> [Barcode：条码/二维码扫描类](https://gitdocument.exmobi.cn/sprite-api/barcode.html) 
> 
> [Camera：拍照，摄像操作类](https://gitdocument.exmobi.cn/sprite-api/camera.html) 


**电话相关**  

> [Phone：电话，短信，邮件操作类](https://gitdocument.exmobi.cn/sprite-api/phone.html)  
> 
> [Contact：通讯录操作类](https://gitdocument.exmobi.cn/sprite-api/contact.html)


**定位相关**  

> [Location：标准定位类](https://gitdocument.exmobi.cn/sprite-api/location.html) 
> 
> [BaiduLocation：百度定位类](https://gitdocument.exmobi.cn/sprite-api/baidulocation.html)
> 
> [GaodeLocation：高德定位类](https://gitdocument.exmobi.cn/sprite-api/gaodelocation.html)


**地图相关**  

> [MapUtil：地图工具类](https://gitdocument.exmobi.cn/sprite-api/maputil.html)
> 
> - 包括：坐标转换，百度地图兴趣点检索，启动导航等   


**硬件相关**  
 

> [Bluetooth：蓝牙通信类](https://gitdocument.exmobi.cn/sprite-api/bluetooth.html) 
> 
> [Nfc：近场通信类](https://gitdocument.exmobi.cn/sprite-api/nfc.html) 
> 
> [TouchId：指纹识别组件](https://gitdocument.exmobi.cn/sprite-api/touchid.html)；


**图片处理**  

> [ImageUtil：图片处理相关类](https://gitdocument.exmobi.cn/sprite-api/imageutil.html) 

**日志相关**

> [Console：日志输出类](https://gitdocument.exmobi.cn/sprite-api/console.html)


**支付相关**  


> [AliPay：支付宝操作类](https://gitdocument.exmobi.cn/sprite-api/alipay.html) 
> 
> [Weixin：微信支付操作类](https://gitdocument.exmobi.cn/sprite-api/weixin.html) 
> 
> [IapPay：苹果虚拟支付工具类](https://gitdocument.exmobi.cn/sprite-api/iappay.html)


**VPN相关**  

> [SangforVpn：深信服vpn类](https://gitdocument.exmobi.cn/sprite-api/sangforvpn.html) 

**分享相关**  

> [Qq：QQ分享操作类](https://gitdocument.exmobi.cn/sprite-api/qq.html) 
> 
> [WeiBo：微博分享操作类](https://gitdocument.exmobi.cn/sprite-api/weibo.html) 
> 
> [WeiXin：微信分享操作类](https://gitdocument.exmobi.cn/sprite-api/weixin.html) 
> 
> [Share：综合分享工具类，提供如一键分享等方法](https://gitdocument.exmobi.cn/sprite-api/share.html)


**推送push**  

> [ExMobiPush  烽火push操作类](https://gitdocument.exmobi.cn/sprite-api/exmobipush.html)
> 
> [JPush：极光Push操作类](https://gitdocument.exmobi.cn/sprite-api/jpush.html)


**IM聊天**  

> [FhIm：烽火Im操作类](https://gitdocument.exmobi.cn/sprite-api/fhim.html) 
> 
> [RlyIm：容联云操作类](https://gitdocument.exmobi.cn/sprite-api/rlyIm.html)

**客服系统**

> [MeiQia:美洽客服SDK操作类](https://gitdocument.exmobi.cn/sprite-api/meiqia.html)


**统计相关**  

> [UmengMtj：友盟日志统计](https://gitdocument.exmobi.cn/sprite-api/umengmtj.html)



**语音合成**  

> [BaiduTts：百度语音合成](https://gitdocument.exmobi.cn/sprite-api/baidutts.html)
> 
> [BaiduVoice：百度语音识别](https://gitdocument.exmobi.cn/sprite-api/baiduvoice.html)

**短信验证码发送**

> [Mob：mob免费短信工具类](https://gitdocument.exmobi.cn/sprite-api/mob.html)  



**ExMobi服务器对接**  

> [AccessAuth：ExMobi服务器鉴权组件类](https://gitdocument.exmobi.cn/sprite-api/accessauth.html) 

**邮件**

> [Mail:邮件相关操作类](https://gitdocument.exmobi.cn/sprite-api/mail.html)


<h2 id="cid_2">js组件打包功能分类</h2>

考虑到实际应用需求，Sprite功能组件分为内置功能组件及外置功能组件，如下表所示：  

> 内置功能组件：Sprite基础包预制功能组件；
> 
> 外置功能组件：构建应用需求选择性添加功能组件；

**内置功能组件**  

> [App](https://gitdocument.exmobi.cn/sprite-api/app.html)
>   
> [Window](https://gitdocument.exmobi.cn/sprite-api/window.html)  
> 
> [Document](https://gitdocument.exmobi.cn/sprite-api/document.html) 
>  
> [Device](https://gitdocument.exmobi.cn/sprite-api/device.html) 
>  
> [Native](https://gitdocument.exmobi.cn/sprite-api/native.html)  
> 
> [Encryption](https://gitdocument.exmobi.cn/sprite-api/encryption.html)  
> [Time](https://gitdocument.exmobi.cn/sprite-api/time.html)  
> 
> [Http](https://gitdocument.exmobi.cn/sprite-api/http.html) 
>  
> [NetInfo](https://gitdocument.exmobi.cn/sprite-api/netinfo.html)  
> 
> [File](https://gitdocument.exmobi.cn/sprite-api/file.html)  
> 
> [UI](https://gitdocument.exmobi.cn/sprite-api/ui.html)
>   
> [MemCache](https://gitdocument.exmobi.cn/sprite-api/memcache.html)  
> 
> [DiskCache](https://gitdocument.exmobi.cn/sprite-api/diskcache.html) 
>  
> [Camera](https://gitdocument.exmobi.cn/sprite-api/camera.html) 
>  
> [Console](https://gitdocument.exmobi.cn/sprite-api/console.html) 
>  
> [Pixel](https://gitdocument.exmobi.cn/sprite-api/pixel.html)
>   
> [ImageUtil](https://gitdocument.exmobi.cn/sprite-api/imageutil.html) 
>  
> [Location](https://gitdocument.exmobi.cn/sprite-api/location.html) 
> 
> [WebSocket](https://gitdocument.exmobi.cn/sprite-api/websocket.html) 
> []()


**外置功能组件**  

> [Db](https://gitdocument.exmobi.cn/sprite-api/db.html) 
>  
> [DbCipher](https://gitdocument.exmobi.cn/sprite-api/dbcipher.html)
>   
> [Barcode](https://gitdocument.exmobi.cn/sprite-api/barcode.html)
>   
> [XmlDocument](https://gitdocument.exmobi.cn/sprite-api/xmldocument.html) 
>  
> [XmlElement](https://gitdocument.exmobi.cn/sprite-api/xmlelement.html)
>   
> [AccessAuth](https://gitdocument.exmobi.cn/sprite-api/accessauth.html)
>   
> [VideoUtil](https://gitdocument.exmobi.cn/sprite-api/videoutil.html)
>   
> [Phone](https://gitdocument.exmobi.cn/sprite-api/phone.html)
>   
> [Sms](https://gitdocument.exmobi.cn/sprite-api/sms.html)
>   
> [Contact](https://gitdocument.exmobi.cn/sprite-api/contact.html)
>   
> [AudioPlay](https://gitdocument.exmobi.cn/sprite-api/audioplay.html) 
>  
> [AudioRecord](https://gitdocument.exmobi.cn/sprite-api/audiorecord.html) 
>  
> [MapUtil](https://gitdocument.exmobi.cn/sprite-api/maputil.html)
>   
> [IapPay](https://gitdocument.exmobi.cn/sprite-api/iappay.html) 
>  
> [WeiXin](https://gitdocument.exmobi.cn/sprite-api/weixin.html) 
>  
> [Qq](https://gitdocument.exmobi.cn/sprite-api/qq.html)
>   
> [WeiBo](https://gitdocument.exmobi.cn/sprite-api/weibo.html)
>   
> [BaiduLocation](https://gitdocument.exmobi.cn/sprite-api/baidulocation.html)
>   
> [AliPay](https://gitdocument.exmobi.cn/sprite-api/alipay.html)
>   
> [BaiduVoice](https://gitdocument.exmobi.cn/sprite-api/baiduvoice.html) 
>  
> [BaiduTts](https://gitdocument.exmobi.cn/sprite-api/baidutts.html) 
>  
> [SanforVpn](https://gitdocument.exmobi.cn/sprite-api/sangforvpn.html)
>   
> [ExMobiPush](https://gitdocument.exmobi.cn/sprite-api/exmobipush.html) 
>  
> [Clipboard](https://gitdocument.exmobi.cn/sprite-api/clipboard.html)
> 
> [Bugly](https://gitdocument.exmobi.cn/sprite-api/bugly.html)
> 
> [RlyIm](https://gitdocument.exmobi.cn/sprite-api/rlyIm.html)
> 
> [JPush](https://gitdocument.exmobi.cn/sprite-api/jpush.html)
> 
> [Pattern](https://gitdocument.exmobi.cn/sprite-api/pattern.html)
> 
> [Share](https://gitdocument.exmobi.cn/sprite-api/share.html)
> 
> [Mob](https://gitdocument.exmobi.cn/sprite-api/mob.html)
> 
> [TouchId](https://gitdocument.exmobi.cn/sprite-api/touchid.html)
> 
> [LocalNotification](https://gitdocument.exmobi.cn/sprite-api/localnotification.html)
> 
> [Agenda](https://gitdocument.exmobi.cn/sprite-api/agenda.html)
> 
> [GaodeLocation](https://gitdocument.exmobi.cn/sprite-api/gaodelocation.html)
> 
> [Nfc](https://gitdocument.exmobi.cn/sprite-api/nfc.html)
> 
> [FhIm](https://gitdocument.exmobi.cn/sprite-api/fhim.html)
> 
> [Bluetooth](https://gitdocument.exmobi.cn/sprite-api/bluetooth.html) 
> 
> [UmengMtj](https://gitdocument.exmobi.cn/sprite-api/umengmtj.html)
> 
> [Mail](https://gitdocument.exmobi.cn/sprite-api/mail.html)
> [MeiQia](https://gitdocument.exmobi.cn/sprite-api/meiqia.html)
> 
> [Gee](https://gitdocument.exmobi.cn/sprite-api/gee.html)
> 
> [GaodeMapUtil](https://gitdocument.exmobi.cn/sprite-api/gaodemaputil.html)
> 
> [X5Util](https://gitdocument.exmobi.cn/sprite-api/x5util.html)
