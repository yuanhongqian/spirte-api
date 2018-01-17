#TouchId  指纹识别工具类


------


TouchId指纹识别工具类，支持iOS8及以上系统且支持指纹识别设备，Android6.0及以上系统且支持指纹识别设备。

TouchId为外置组件。

<h2 id="cid_1">方法</h2>

本节目录：

> [isSupportTouch():boolean 当前设备是否支持指纹识别](#ff_1)
> 
> [verify(jsonData:Object,callbackFun:Function):void](#ff_2)
> 
> [isKeyguardSecure():boolean 当前设备是否开启锁屏密码](#ff_3)
> 
> [isEnrolledFingerprints():boolean 当前设备是否有指纹录入](#ff_4)
> 
> [cancelVerify():void 取消Android设备密码验证](#ff_5)
> 
> [openConfirmDevice(callbackFun:Function):void 打开Android锁屏验证界面](#ff_6)


<span id="ff_1">**isSupportTouch():boolean**</span>

<code>当前设备是否支持指纹识别</code>

参数：无

返回值：bool型。true：设备支持指纹识别；false：设备不支持指纹识别

<span id="ff_2">**verify(jsonData:Object,callbackFun:Function)**</span>

<code>启动设备指纹识别</code>

启动设备指纹识别，iOS弹出系统指纹识别界面，Android后台识别

参数：

jsonData：json格式，定义如下：

> title：iOS弹出设备指纹识别验证界面的标题，可选项；
> 
> failbackTitle：iOS设置指纹输入失败后弹出框右侧按钮显示文字，可选项

callbackFun：指纹识别回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字
> 
> **Android**
> 
> - 0：指纹验证成功；
> 
> - -1：指纹验证失败；
> 
> - -2：指纹验证错误，即连续验证失败6次则进该回调，收到该回调后指纹验证功能失效，需要openConfirmDevice()打开锁屏密码界面来进行验证；
> 
> - -3：设备本身并不具备指纹传感装置
> 
> - -4：设备未开启锁屏密码
> 
> - -5：设备未录入指纹
> 
> - -6：用户取消指纹录入
> 
> - 其他：其他错误
> 
> **iOS**
> 
> - 0：指纹验证成功；
> 
> - -1：指纹验证失败；
> 
> - -2：用户点击取消
> 
> - -3：用户点击输入密码
> 
> - -4：其他应用切换至前台导致验证失败
> 
> - -5：设备未设置指纹密码
> 
> - -6：设备本身并不具备指纹传感装置
> 
> - -7：已经设定有密码机制，但设备配置当中还没有保存过任何指纹内容
> 
> - -8：指纹验证错误，即连续验证失败5次后进该回调，对于iOS9系统，若再次验证，系统会弹出输入数字密码的页面，iOS10下次验证则继续返回该状态码，需通过Native.openSystemSetting()打开系统密码设置界面重新设置
> 
> result：错误消息描述，字符串类型，当code为非0时有效

返回值：无

<span id="ff_3">**isKeyguardSecure():boolean **</span>

<code>当前设备是否开启锁屏密码</code>

参数：无

返回值：boolean型。true：设备开启锁屏密码；false：设备未开启锁屏密码

注：仅Android支持

<span id="ff_4">**isEnrolledFingerprints():boolean**</span>

<code>当前设备是否有指纹录入</code>

参数：无

返回值：boolean型。true：设备已录入指纹；false：设备未录入指纹

注：仅Android支持

<span id="ff_5">**cancelVerify():void**</span>

<code>取消Android设备密码验证</code>

参数：无

返回值：无

注：仅Android支持

<span id="ff_6">**openConfirmDevice(callbackFun:Function):void**</span>

<code>打开Android锁屏验证界面</code>

参数：

callbackFun：锁屏验证回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字。0：锁屏验证成功；-1：取消锁屏验证

返回值：无

注：仅Android支持