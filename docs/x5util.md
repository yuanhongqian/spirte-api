# X5Util 工具类


-----------------

X5Util工具类，实现x5webview调用相关方法，仅Android支持。

注：X5Util为外置组件。

<h2 id="cidd_1">方法</h2>

本节目录：

> [initX5Environment(callback:Function):void 初始化X5内核](#ff_0)
> 
> [canUseTbsPlayer():boolean 判断当前X5Tbs播放器是否已经可以使用](#ff_1)
> 
> [openVideo(jsonData:Object):void 调用Tbs播放器打开视频](#ff_2)

<span id="ff_0">**initX5Environment(callback:Function):void**</span>

<code>初始化X5内核</code>

参数：

callback：加载图片回调，该回调函数具有json对象入参，定义如下：

> code：回应状态码，数字【0，-1】，0：初始化成功；-1：初始化失败；

返回值：无

注：X5内核预加载接口，建议在进入x5webview场景前调用该接口提升x5内核使用率和优化冷启动耗时

<span id="ff-1">**canUseTbsPlayer():boolean**</span>

<code>判断当前X5Tbs播放器是否已经可以使用</code>

参数：无

返回值：boolean型，true：播放器可使用，false：播放器不可使用



<span id="ff_2">**openVideo(jsonData:Object):void **</span>

<code>调用Tbs播放器打开视频</code>

参数：

jsonData：传递参数，json格式，定义如下：

> videoPath：需要播放视频路径，字符串类型，本地路径，res：、file：前缀，网络路径：http:前缀，必选项；

注：Tbs视频播放器可以支持市面上几乎所有的视频格式，包括mp4，flv，avi，3gp，webm，ts，ogv，m3u8，asf，wmv，rm，rmvb，mov，mkv等18种视频格式。


