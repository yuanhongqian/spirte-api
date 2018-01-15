#  WebSocket 组件

----------
WebSocket是一种在单个TCP连接上就那些全双工通讯的协议，这使得客户端应用和服务器之间打开一个交互式通讯会话成为可能，使用WebSocket，你可以向服务器发送消息，并接收事件驱动的响应，无需轮询服务器的响应。 

WebSocket为多例内置组件，通过构造函数构建：


```javascript
var socketObj = new WebSocket(); 
```


<h2 id="cid_1">js方法</h2>  

本节目录：

> [connect(jsondata:Object):void 建议WebSocket](#ff_0)
> 
> [send(data:String):void 通过WebSocket连接向服务器发送数据](#ff_1)
> 
> [close():void 关闭websocket连接](#ff_2)
> 
> [getReadyState():number 获取WebSocket当前连接状态](#ff_3)


<span id="ff_0">**connect(jsondata:Object):void**</span>  

<code>建议WebSocket</code>  

参数： 

jsonData：设置参数，Json对象，定义如下：  
> url：需要连接的WebSocket服务器URL地址，前缀ws://或wss://，字符串类型，必选项，如：ws://echo.websocket.org

 
返回值：无


<span id="ff_1">**send(data:String):void**</span>

<code>通过WebSocket连接向服务器发送数据</code>

参数：

data：要发送服务器的数据，字符串类型

返回值：无

<span id="ff_2">**close():void**</span>

<code>关闭websocket连接</code>

参数：无

返回值：无

注：客户端直接调用close方法并不会关闭连接，而是发送请求到服务器请求对方，服务器接收请求后可以断开连接。这会触发客户端的close事件


<span id="ff_3">**getReadyState():number**</span>

<code>获取WebSocket当前连接状态</code>

参数：无


返回值：WebSocket当前连接状态，数字类型，表示连接状态，可以是以下值：
> 0 表示连接尚未建立
> 
> 1 表示连接已建立，可以进行通信
> 
> 2 表示连接正在进行关闭
> 
> 3 表示连接已经关闭或者连接不能打开



<h2 id="cid_2">事件</h2> 

**onopen**

<code>连接建立时触发</code>

event事件对象包括：

> type：事件类型，字符串类型，固定值：onopen
> 
> target：触发事件的目标组件
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型


**onmessage**

<code>客户端接收服务端数据时触发</code>

event事件对象包括：

> type：事件类型，字符串类型，固定值：onmessage；
> 
> target：触发事件的目标组件
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型
> 
> data：接收到的服务端数据，字符串类型


**onerror**

<code>通信发生错误时触发</code>

event事件对象包括：

> type：事件类型，字符串类型，固定值：onerror；
> 
> target：触发事件的目标组件，dom对象
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型
> 
> data：错误信息描述，字符串类型


**onclose**

<code>连接关闭时触发</code>

event事件对象包括：

> type：事件类型，字符串类型，固定值onclose
> 
> target：触发事件的目标组件，dom对象
> 
> timestamp：事件触发的时间戳，单位毫秒，数字类型
