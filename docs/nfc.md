#  Nfc组件使用


-------

Nfc组件封装Android系统对NFC标签中标准NDEF格式的数据读写操作，目前支持NdefRecordType为TEXT格式。

Nfc为外置组件

<h2 id="cid_1">方法</h2>

本节目录：

> [isSupport():boolean 判断设备是否支持NFC功能](#ff_0)
> 
> [isOPen():boolean 判断设备NFC是否打开](#ff_1)
> 
> [start():boolean 开始扫描NFC设备](#ff_2)
> 
> [stop():boolean 关闭扫描NFC设备](#ff_3)
> 
> [write(jsonData:Object,callbackFun:Function):void 向NFC设备写入数据](#ff_4)




<span id="ff_0">**isSupport():boolean**</span>

<code>判断设备是否支持NFC功能</code>

参数：无

返回值：boolean型，true：设备支持Nfc，false：设备不支持Nfc

<span id="ff_1">**[isOPen():boolean**</span>

<code>判断设备NFC是否打开</code>

参数：无

返回值：boolean型，true：设备Nfc已打开，false：设备Nfc未打开

注：若设备NFC未打开，则可调用Native.openSystemSetting()跳转至NFC设置界面告知用户手动开启

<span id="ff_2">**start():boolean**</span>

<code>开始扫描NFC设备</code>

参数：无

返回值：boolean型，true：进入扫描NFC状态，false：未进入扫描NFC状态

注：开启扫描成功后，将支持NFC的卡片放在设备感应区附近即可接收到数据并进入received回调事件中


<span id="ff_3">**stop():boolean**</span>

<code>关闭扫描NFC设备</code>

参数：无

返回值：boolean型，true：关闭扫描NFC状态，false：未关闭扫描NFC状态

注：用户取消扫描NFC时必须调用该接口


<span id="ff_4">**write(jsonData:Object,callbackFun:Function):void**</span>

<code>向NFC设备写入数据</code>

参数：

jsonData：传递参数，json类型，必选项，定义如下：

> data：需写入的Nfc设备的数据，字符串类型，必选项；

callbackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】。0：写入NFC标签成功；-1：写入NFC标签失败；
> 
> id：写入NFC标签id标识，字符串类型


返回值：无


<h2 id="cid_2">事件</h2>

**received**

<code>读取Nfc卡数据后触发</code>

event事件对象包括：

> type：事件类型，字符串类型，固定值：received；
> 
> target：触发事件的目标组件；
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型
> 
> id：读取Nfc标签id，字符串类型
> data：读取到Nfc标签数据，字符串类型