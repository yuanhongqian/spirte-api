# Bluetooth 蓝牙组件

----------

Bluetooth封装了蓝牙4.0功能，开发者使用该组件可实现基础的蓝牙数据交互。系统要求：Android：4.3及以上，iOS：8.0及以上。  

Bluetooth为外置组件


<h2 id="cid_1">方法</h2>

本节目录：
> [init(function:Function):void 初始化蓝牙4.0管理器](#ff_0)
> 
> [openBluetooth(function:Function):void 打开蓝牙](#ff_1)
> 
> [scan(dataJson:Object,function:Function):void 开始搜索蓝牙4.0设备](#ff_2)
> 
> [stopScan():void 停止搜索附件的蓝牙设备](#ff_3)
> 
> [connect(jsonData:Object,function:Function):void 连接指定外围设备](#ff_4)
> 
> [disconnect(jsonData:Object,function:Function):void 断开与指定外围设备的连接](#ff_5)
> 
> [connectPeripherals(jsonData:Object,function:Function):void 连接多台外围设备](#ff_6)
> 
> [isConnected(jsonData:Object):boolean 判断与指定外围设备是否为连接状态](#ff_7)
> 
> [discoverService(jsonData:Object,function:Function):void 根据指定的外围设备UUID获取该外围设备的所有服务](#ff_8)
> 
> [setNotify(jsonData:Object,function:Function):void 根据指定的外围设备UUID及其服务UUID和特征UUID监听](#ff_9)
> 
> [stopNotify(jsonData:Object,function:Function):void 根据指定的外围设备UUID及其服务UUID和特征UUID停止监听数据](#ff_10)
> 
> [read(jsonData:Object,function:Funciton):void 根据指定的外围设备UUID及其服务UUID和特征UUID进行数据监听](#ff_11)
> 
> [write(jsonData:Object,funtion:Function):void 根据指定的外围设备UUID及其服务UUID和特征UUID发送数据](#ff_12)

<span id="ff_0">**init(function:Function):void**</span>

<code>初始化蓝牙4.0管理器</code>

初始化蓝牙4.0管理器，处理结果进入回调中返回

参数：

function：初始化回调函数，该函数具有json类型入参，入参定义如下：

> state：蓝牙4.0设备连接状态，取值范围如下，字符串枚举型，【powered_on,powered_off,resetting,unauthorized,unknown,unsupported】，说明如下：
> 
> - powered_on：设备开启状态--可用状态
> 
> - powered_off：设备关闭状态
> 
> - resetting：正在重置状态
> 
> - unauthorized：设备未授权状态
> 
> - unknown：初始的时候是未知的
> 
> - unsupported：设备不支持的状态

返回值：无


<span id="ff_1">**openBluetooth(function:Function):void**</span>

<code>打开蓝牙</code>

打开蓝牙，处理结果进入回调中返回

参数：

function：打开蓝牙回调函数，该函数具有json类型入参，入参定义如下：

> code：数字，【0，-1】，0：打开蓝牙成；-1：打开蓝牙失败

返回值：无

注：仅Android支持

<span id="ff_2">**scan(dataJson:Object,function:Function):void**</span>

<code>开始搜索蓝牙4.0设备</code>

开始搜索蓝牙4.0设备，模块内部会不断的扫描更新附近的蓝牙4.0设备信息，扫描结果进入scanNotify事件中

参数：

dataJson：传递参数，json格式，定义如下：

> peripheralUUIDs:要扫描的蓝牙4.0设备的服务（service）的UUID，若不传则扫描附件的所有支持蓝牙4.0的设备，数组类型，数组元素为字符串，可选参数，注：该参数系统iOS扫描的是具有广播属性设备的serviceUUID，Android扫描的是MAC地址；

function：搜索蓝牙4.0设备回调函数，函数具有json类型入参，入参定义如下：

> code：启动扫码回应状态码，数字【0，-1】。0：启动成功；-1：启动扫码失败；

返回值：无

<span id="ff_3">**stopScan():void**</span>

<code>停止搜索附近的蓝牙设备</code>

参数：无

返回值：无


<span id="ff_4">**connect(jsonData:Object,function:Function):void **</span>

<code>连接指定外围设备</code>

参数：

jsonData：连接参数，json格式，定义如下：

> peripheralUUID：要连接的外围设备的UUID，字符串，必选项

function：连接指定外围设备，回调函数，该函数具有json类型入参，入参定义如下：

> code：连接指定外围设备回应状态码，数字【0，-1】。0：连接成功；-1：连接失败

返回值：无

<span id="ff_5">**disconnect(jsonData:Object,function:Function):void**</span>

<code>断开与指定外围设备的连接</code>

参数：

jsonData：断开连接传递数据，json格式，定义如下：

> peripheralUUID：要断开的外围设备的UUID，字符串，必选参数；

function：断开连接的外围设备回调函数，该函数具有json类型入参，入参定义如下：

> code：连接指定外围设备回应状态码，数字【0，-1】。0：连接成功；-1：连接失败

返回值：无


<span id="ff_6">**connectPeripherals(jsonData:Object,function:Function):void**</span>

<code>连接多台外围设备</code>

参数：

jsonData：传递参数，json格式，定义如下：

> peripheralUUIDs：要连接的外围设备的UUID字符串组成的数组，注：该参数系统iOS扫描的是具有广播属性设备的serviceUUID，Android扫描的是MAC地址；

function：连接回调函数，peripheralUUIDs传入多少个id则本回调执行多少次，该函数具有json类型入参，入参定义如下：

> code：连接指定外围设备回应状态码，数字【0，-1】。0：连接成功；-1：连接失败
> 
> peripheralUUID：所要连接的外围设备的id，字符串类型

返回值：无


<span id="ff_7">**isConnected(jsonData:Object):boolean **</span>

<code>判断与指定外围设备是否为连接状态</code>

参数：

jsonData：传递数据，json格式，定义如下：

> peripheralUUID：要连接的外围设备的UUID，字符串，必选参数，注：该参数系统iOS扫描的是具有广播属性设备的serviceUUID，Android扫描的是MAC地址

返回值：是否连接，boolean型，true：连接状态，false：非连接状态

<span id="ff_8">**discoverService(jsonData:Object,function:Function):void**</span>

<code>根据指定的外围设备UUID获取该外围设备的所有服务</code>

参数：

jsonData：获取该外围设备的所有服务传递参数，json格式，定义如下：

> peripheralUUID：指定的蓝牙外围设备的UUID，字符串类型，必选参数，注：该参数系统iOS扫描的是具有广播属性设备的serviceUUID，Android扫描的是MAC地址

function：查获取该外围设备的所有服务回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1，1，2】
> 
> - 0：获取成功；
> 
> - -1：位置错误
> 
> - 1：perihperalUUID为空
> 
> - 2：尚未搜索到该蓝牙设备
> 
> services：获取的所有服务号集合，数组类型，数组元素为字符串；
> 
> characteristics：获取的所有特征信息的集合，数组类型，数组元素为json格式，定义如下：
> 
> - characteristicUUID：特征的UUID，字符串类型；
> 
> - serviceUUID：服务的UUID，字符串类型；
> 
> - properties：特征的属性，字符串枚举型【broadcast，read，write_without_response,write,notify,indicate,authenticated_signed_writes,extended_properties】，说明如下：
> 
>  - broadcast：具备广播属性，字符串类型；
>  - read：具备可读属性，字符串类型；
>  - write_without_response：具备无响应的写入属性，字符串类型；
>  - write：具备可写入属性，字符串类型；
>  - notify：具备通知属性，字符串类型；
>  - indicate：具备显示属性，字符串类型；
>  - authenticated_signed_writes：具备签名写入属性，字符串类型；
>  - extended_properties：具备扩展属性，字符串类型；
>  
> descriptors：获取的所有描述符信息的集合，数组类型，数组元素为json格式，定义如下：
> - descriptorUUID：描述符的UUID，字符串类型
> 
> - serviceUUID：服务的UUID，字符串类型
> 
> - characteristicUUID：指定特征的UUID，字符串类型；

返回值：无

<span id="ff_9">**setNotify(jsonData:Object,function:Function):void**</span>

<code>监听</code>

根据指定的外围设备UUID及其服务UUID和特征UUID监听

参数：

jsonData：监听数据传递参数，json格式，定义如下：

> peripheralUUID：指定的蓝牙外围设备的UUID，字符串类型，必选参数，注：该参数系统iOS扫描的是具有广播属性的serviceUUID，Android扫描的是MAC地址；
> serviceUUID：指定的服务的UUID，字符串类型，必选参数；
> 
> characteristicUUID：指定的特征的UUID，必选参数

function：监听数据回调函数，每有数据接收便会触发此回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字，【0，-1，1，2，3，4，5，6】，说明如下：
> - 0：获取成功
> 
> - -1：未知错误
> 
> - 1：peripheralUUID为空
> 
> - 2：serviceUUID为空
> 
> - 3：characteristicUUID为空
> 
> - 4：未找到指定特征（characteristic）
> 
> - 5：未找到指定服务（service）
> 
> - 6：尚未搜索到该蓝牙设备
> 
> characteristics：获取的所有特征信息，json格式，定义如下：
> 
> - characteristicUUID：特征的UUID，字符串类型；
> 
> - serviceUUID：服务的UUID，字符串类型；
> 
> - properties：特征的属性，字符串枚举型【broadcast，read，write_without_response，write，notify，indicate，authenticated_signed_writes,extended_properties】，说明如下：
> 
>  - broadcast：具备广播属性，字符串类型；
>  
>  - read：具备可读属性，字符串类型；
>  
>  - write_without_response：具备无响应的写入属性，字符串类型
>  
>  - write：具备可写入属性，字符串类型；
>  
>  - notify：具备通知属性，字符串类型
>  
>  - indicate：具备显示属性，字符串类型；
>  
>  - authenticated_signed_writes：具备签名写入属性，字符串类型
>  
>  - extended_properties：具备扩展属性，字符串类型

返回值：无


<span id="ff_10">**stopNotify(jsonData:Object,function:Function):void **</span>

<code>停止监听数据</code>

根据指定的外围设备UUID及其服务UUID和特征UUID停止监听数据

参数：

jsonData：监听数据传递参数，json格式，定义如下：

> peripheralUUID：指定的蓝牙外围设备的UUID，字符串类型，必选参数，注：该参数系统iOS扫描的是具有广播属性设备的serviceUUID，Android扫描的是MAC地址；
> 
> serviceUUID：指定的服务器的UUID，字符串类型，必选参数；
> 
> characteristicUUID：指定的特征的UUID，必选参数

function：获取登录后该用户所属群组回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字，【0，-1】。0：成功；-1：失败

返回值：无


<span id="ff_11">**read(jsonData:Object,function:Funciton):void**</span>

<code>数据监听</code>

根据指定的外围设备UUID及其服务UUID和特征UUID进行数据监听

参数：

jsonData：读取数据传递参数，json格式，定义如下：

> peripheralUUID：指定的蓝牙外围设备的UUID，字符串类型，必选参数，注：该参数系统iOS扫描的是具有广播属性设备的serviceUUID，Android扫描的是MAC地址
> serviceUUID：指定的服务的UUID，字符串类型，必选参数；
> characteristicUUID：指定的特征的UUID，字符串类型，必选参数；

function：读取数据回调函数，每有数据接收便会触发回调，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字，【0，-1，1，2，3，4，5，6】
> - 0：获取成功；
> 
> - -1：未知错误；
> 
> - 1：peripheralUUID为空
> 
> - 2：serviceUUID为空
> 
> - 3：characteristicUUID为空
> 
> - 4：未找到指定特征（characteristic）
> 
> - 5：未找到指定服务（service）
> 
> - 6：尚未搜索到该蓝牙设备
> 
> peripheralUUID：指定的蓝牙外围设备的UUID，字符串类型
> 
> serviceUUID：指定的服务的UUID，字符串类型；
> 
> characteristicUUID：指定的特征的UUID，字符串类型
> 
> value：读取的数据，字符串类型

返回值：无


<span id="ff_12">**write(jsonData:Object,funtion:Function):void** </span>

<code>发送数据</code>

根据指定的外围设备UUID及其服务UUID和特征UUID发送数据

参数：

jsonData：发送数据传递参数，json格式，定义如下：

> peripheralUUID：指定的蓝牙外围设备的UUID，字符类型，必选参数，注：该参数系统iOS扫描的是具有广播属性设备的serviceUUID，Android扫描的是MAC地址；
> 
> serviceUUID：指定的服务的UUID，字符串类型，必选参数；
> 
> characteristicUUID：指定的特征的UUID，字符串类型，必选参数；
> 
> data：要写入的数据，字符串类型，必选参数；
> 
> writeType：写入数据时的类型，可选，字符串枚举型【auto，response，without_response】
> 
> - auto：模块自动选择类型（默认）；
> 
> - response：有回调；
> 
> - without_response：无回调

function：发送数据回调函数，该函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1，1，2，3，4，5，6，7】
> - 0：发送成功；
> 
> - -1：未知错误；
> 
> - 1：peripheralUUID为空
> 
> - 2：serviceUUID为空
> 
> - 3：characteristicUUID为空
> 
> - 4：value为空
> 
> - 5：未找到指定特征（characteristic）
> 
> - 6：未找到指定服务（service）
> 
> - 7：尚未搜索到该蓝牙设备
> 
> peripheralUUID：指定的蓝牙外围设备的UUID，字符串类型
> 
> serviceUUID：指定的服务的UUID，字符串类型
> 
> characteristicUUID：指定的特征的UUID，字符串类型；

返回值：无


<h2 id="cid_2">事件</h2>

**scanNotify**

<code>搜索蓝牙4.0设备通知</code>

搜索蓝牙4.0设备通知，当搜索到设备后触发

event事件对象包括：

> type：事件类型，字符串类型，固定值：scanNotify；
> target：触发事件的目标组件
> timestamp：事件触发的时间戳，单位毫秒，数字类型

param对象为json对象，定义如下：

> peripherals：对象为扫描到的设备信息集合，数组类型，数组元素为json格式
> - peripheralUUID：蓝牙外围设备的UUID，字符串
> 
> - name：设备的蓝牙昵称，字符串
> 
> - rssi：设备蓝牙信号强度，数字
