#  GaodeLocation 高德定位类

----------
GaodeLocation 高德定位类，封装了高德定位SDK。高德定位SDK为移动端应用提供了一套简单易用的定位服务接口，通过使用高德定位SDK，开发者可以轻松为应用程序实现智能、精准、高效的定位功能。高德定位可单独使用定位，也可与gaodemap/baidumap UI组件配合使用，进行地图定位。

开发者需先去高德地图开发平台申请开发者账号，创建应用所对应的appKey。

Android和iOS平台请分别申请Key进行配置

Android：[http://lbs.amap.com/api/android-location-sdk/guide/create-project/get-key](http://lbs.amap.com/api/android-location-sdk/guide/create-project/get-key)

iOS：[http://lbs.amap.com/api/ios-location-sdk/guide/create-project/get-key](http://lbs.amap.com/api/ios-location-sdk/guide/create-project/get-key)




在官方平台打包的sprite客户端签名证书的sha1值为：
```
0D:ED:5B:2A:C3:C6:40:44:B4:8C:97:EF:2B:FB:7E:6A:6C:86:24:47 
```
包名以实际打包的为准，如：com.fiberhome.sprite.client。

使用时需要在js中引入 ：

```javascript
var gaodelocation = require("GaodeLocation"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

> [start(jsonData:Object): void   启动定位 ](#ff_0)
> 
> [isStarted(): boolean 高德定位是否正在运行 ](#ff_1)
>
> [stop(): void   关闭高德定位 ](#ff_2)



<span id="ff_0">**start(jsonData:Object): void**</span>  

<code>启动定位</code>  

启动定位，定位结果进入receiveLocation事件中

参数：  

jsonData：Json对象，Android和iOS存在系统差异，分别定义如下：  

**Android**

> mode：定位模式，字符串枚举型，[Hight_Accuracy, Battery_Saving, Device_Sensors]，可选项  
> 
> - Hight_Accuracy：高精度定位模式，这种定位模式下，会同时使用网络定位和GPS定位，优先返回最高精度的定位结果（默认）；
> 
> - Battery_Saving：低功耗定位模式，这种定位模式下，不会使用GPS，只会使用网络定位，Wi-Fi和基站定位； 
> 
> - Device_Sensors：仅用设备定位模式：这种定位模式下，不需要连接网络，只使用GPS进行定位，这种模式下不支持室内环境的定位；
> 
> isOnce：是否单次定位，boolean型，true：单次（默认）；false：持续定位
> 
> interval：持续定位时间间隔，数字类型，单位毫秒，默认2000ms
> 
> needAddress：是否需要地址信息，boolean型，可选项。true：需要（默认）；false：不需要；
> 
> wifiActiveScan：是否强制刷新WIFI，boolean型，可选项。true：强制刷新（默认）；false：不刷新
> 
> timeOut：定位超时时间，数字，单位：秒。可选项，默认值30s，建议超时时间不要低于8s
> 
> locationCache：是否开启定位缓存机制，boolean型，true：开启定位缓存（默认）；false：不开启缓存，当开启定位缓存功能，在高精度模式和低功耗模式下进行的网络定位结果均会生成本地缓存，不区分单次定位还是连续定位。GPS定位结果不会被缓存。
> 
> protocol：设定网络定位时所采用的协议，提供http/https两种协议，字符串枚举型，可选项，【http,https】，http：网络定位采用http协议（默认）；https：网络定位采用https协议；

**iOS**

> accuracy：定位精度，字符串枚举型，可选项，【BestForNavigation，Best，NearestTenMeters，HundredMeters，Kilometer，ThreeKilometers】
> - BestForNavigation：最适合导航
> 
> - Best：最优精度（默认）
> 
> - NearestTenMeters：精度10m
> 
> - HundredMeters：精度100m
> 
> - Kilometer：精度1000m
> 
> - ThreeKilometers：精度3000m
> 
> distanceFilter：设定定位的最小更新距离，数字类型，单位米，可选项，默认。只要检测到设备位置发生变化就会更新位置信息。
> 
> background：是否允许后台定位，boolean型，可选项，默认false。只在iOS9.0及之后起作用。设置为YES的时候必须保证BackgroundModes中的Location updates处于选择状态，否则会抛出异常。由于iOS系统限制，需要再定位未开始之前或定位停止之后，修改该属性的值才会有效果。
> 
> needAddress：是否需要地址信息，boolean型，可选项，true：需要（默认）；false：不需要
> 
> isOnce：是否单次定位，boolean型，true：单次（默认）；false：持续定位
> 
> locationTimeout：单次定位超时时间，数字类型，单位秒，可选项，默认为10s。最小值是2s
> 
> reGeocodeTimeout：单次定位逆地理超时时间，数字类型，单位秒，可选项，默认为5s。最小值是2s。


返回值：无



<span id="ff_1">**isStarted(): boolean**</span>  

<code>高德定位是否正在运行</code>   

参数：无 

返回值：bool型  

> true：高德定位已启动
> 
> false：高德定位未启动

<span id="ff_2">**stop(): void**</span>  

<code>关闭高德定位</code>  

参数：无  

返回值：无



<h2 id="cid_2">事件</h2>  


**receiveLocation**

<code>接收高德定位结果回调</code>

event事件对象包括：  

> type：事件类型，字符串类型，固定值：receiveLocation；
> 
> target：触发事件的目标组件 
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param对象为Json对象，定义如下：

> code：回应状态码，数字
> 
> -  0：定位成功
> 
> - -1：定位失败 
> 
> Longitude：坐标经度，数字  
> 
> latitude：坐标纬度，数字
> 
> accuracy：定位精度，数字，单位：米
> 
> direction：方向，数字，0-360，未获取返回-1
> 
> speed：速度，数字，单位：m/s，定位类型为gps时可用，未获取返回-1
>  
> altitude：海拔高度，数字，单位：米，定位类型为gps时可用
>  
> country：国家，字符串
> 
> province：省，字符串
> 
> cityCode：城市码，字符串
> 
> city：城市，字符串
> 
> district：区，字符串
> 
> street：街道，字符串
> 
> streetNum：街道门牌号，字符串 
> 
> address：地址信息，字符串
> 
> poiName：获取当前位置的POI名称，字符串类型
> 
> aoiName：获取当前位置的AOI名称，字符串类型
> 
> locationType：获取定位结果来源，数字枚举型，【1，2，4，5，6，8】
> - 1：GPS定位结果，通过设备GPS定位模块返回的定位结果，精度较高，在10米-100米左右
> 
> - 2：前次定位结果，网络定位请求低于1秒，或两次定位之间设备位置变化非常小时返回，设备位移通过传感器感知
> 
> - 4：缓存定位结果，返回一段时间前设备在同样的位置缓存下来的网络定位结果
> 
> - 5：Wifi定位结果，属于网络定位，定位精度相对基站定位会更好，定位精度较高，在5米-200米之间
> 
> - 6：基站定位结果，纯碎依赖移动、联通、电信等移动网络定位，定位精度在500米-5000米之间
> 
> - 8：离线定位结果。
> 
> locationDetail：定位信息描述，字符串类型
> 
> errorCode：定位错误码，数字，详见[高德官网错误码说明](http://lbs.amap.com/api/android-location-sdk/guide/utilities/errorcode/)，仅Android支持
> 
> errorInfo：定位错误描述，字符串类型，详见[高德官网错误码说明](http://lbs.amap.com/api/android-location-sdk/guide/utilities/errorcode/)，仅Android支持
 




