#  BaiduLocation 百度定位类

----------
BaiduLocation 百度定位类基于百度提供SDK进行封装集成，可单独使用定位，也可与baidumap UI组件配合使用，进行地图定位。

使用百度地图定位功能标准版已经内置百度key值，如果开发者自行打包后，需要自己去百度地图官网申请对应key值。

在官方平台打包的sprite客户端签名证书的sha1值为：
```
0D:ED:5B:2A:C3:C6:40:44:B4:8C:97:EF:2B:FB:7E:6A:6C:86:24:47 
```
包名以实际打包的为准，如：com.fiberhome.sprite.client。

使用时需要在js中引入 ：

```javascript
var baidulocation = require("BaiduLocation"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

> [start(jsonData:Object): void   启动定位 ](#ff_0)
> 
> [isStarted(): boolean 百度定位是否正在运行 ](#ff_1)
>
> [stop(): void   百度定位是否正在运行 ](#ff_2)



<span id="ff_0">**start(jsonData:Object): void**</span>  

<code>启动定位</code>  

启动定位，定位结果进入receiveLocation事件中

参数：  

jsonData：Json对象，定义如下：  

> mode：定位模式，字符串枚举型，[Hight_Accuracy, Battery_Saving, Device_Sensors]，可选项，仅Android支持；  
> 
> Hight_Accuracy：高精度定位模式，这种定位模式下，会同时使用网络定位和GPS定位，优先返回最高精度的定位结果（默认）；
> 
> Battery_Saving：低功耗定位模式，这种定位模式下，不会使用GPS，只会使用网络定位，Wi-Fi和基站定位； 
> 
> Device_Sensors：仅用设备定位模式：这种定位模式下，不需要连接网络，只使用GPS进行定位，这种模式下不支持室内环境的定位；
> 
> coorType：坐标系类型，字符串枚举型，可选项，[bd09ll,wgs84,gcj02]，仅Android支持，iOS固定为bd09ll百度地图坐标系
> 
> - bd09ll：百度地图坐标系
> 
> - wgs84：标准gps坐标系
> 
> - gcj02：由中国国家测绘局制订的地理信息系统的坐标系统（默认）
> 
> scanSpan：定位间隔，数字，可选项，单位ms，默认为0即只定位一次，设置发起定位请求的间隔需要大于等于1000ms才有效，仅Android支持
> 
> timeOut：定位超时时间，数字，单位：秒，可选项，默认值60
> 
> openGps：是否需要使用gps，bool型，可选项，true：需要；false：不需要（默认），仅Android支持
> 
> needAddress：是否需要地址信息，bool型，可选项，true：需要；false：不需要（可选），仅Android支持
> 
> 
> needLocationDescribe：设置是否需要位置语义化结果，bool型，可选项，true：需要；false：不需要（默认），仅Android支持

返回值：无



<span id="ff_1">**isStarted(): boolean**</span>  

<code>百度定位是否正在运行</code>   

参数：无 

返回值：bool型  

> true：百度定位已启动
> 
> false：百度定位未启动

<span id="ff_2">**stop(): void**</span>  

<code>关闭百度定位</code>  

参数：无  

返回值：无



<h2 id="cid_2">事件</h2>  


**receiveLocation**

<code>接收百度定位结果回调</code>

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
> locType：定位结果返回码，数字枚举型，仅Android支持，根据百度sdk定义如下：  
> 
> - 61：GPS定位结果，GPS定位成功。
> 
> - 62：无法获取有效定位依据，定位失败，请检查运营商网络或者WiFi网络是否正常开启，尝试重新请求定位。
> 
> - 63：网络异常，没有成功向服务器发起请求，请确认当前测试手机网络是否通畅，尝试重新请求定位。
> 
> - 65：定位缓存的结果。
> 
> - 66：离线定位结果。通过requestOfflineLocaiton调用时对应的返回结果。
> 
> - 67：离线定位失败。通过requestOfflineLocaiton调用时对应的返回结果。
> 
> - 68：网络连接失败时，查找本地离线定位时对应的返回结果。
> 
> - 161：网络定位结果，网络定位成功。
> 
> - 162：请求串密文解析失败，一般是由于客户端SO文件加载失败造成，请严格参照开发指南或demo开发，放入对应SO文件。
> 
> - 167：服务端定位失败，请您检查是否禁用获取位置信息权限，尝试重新请求定位。
> 
> - 502：AK参数错误，请按照说明文档重新申请AK。
> 
> - 505：AK不存在或者非法，请按照说明文档重新申请AK。
> 
> - 601：AK服务被开发者自己禁用，请按照说明文档重新申请AK。
> 
> - 602：key mcode不匹配，您的AK配置过程中安全码设置有问题，请确保：SHA1正确，“;”分号是英文状态；且包名是您当前运行应用的包名，请按照说明文档重新申请AK。
> 
> - 501～700：AK验证失败，请按照说明文档重新AK
> 
> coorType：坐标系类型，字符串枚举型，[bd09ll,wgs84,gcj02]
> 
> longitude：坐标经度，数字
> 
> latitude：坐标纬度，数字
> 
> radius：定位半径，数字，单位：米
> 
> direction：方向，数字，0-360
> 
> speed：速度，数字，单位：km/h，定位类型为gps时可用，未获取返回-1
> 
> altitude：海拔高度，数字，单位：米，定位类型为gps时可用
> 
> countryCode：国家码，字符串，仅Android支持
> 
> country：国家，字符串，仅Android支持
> 
> cityCode：城市码，字符串，仅Android支持
> 
> city：城市，字符串，仅Android支持
> 
> district：区，字符串，仅Android支持
> 
> street：街道，字符串，仅Android支持
> 
> address：地址信息，字符串，仅Android支持
> 
> locationDescribe：位置语义化信息，字符串，仅Android支持
> 
> satelliteNumber：卫星数目，数字，定位类型为gps或network可用，仅Android支持
> 
> gpsAccuracyStatus：gps质量判断，数字，定位类型为gps时可用，仅Android支持
> 
> operators：运营商信息，数字，定位类型为 network时可用，仅Android支持

**注： ** 由于ios的百度定位sdk没有提供详细地理位置信息， ios如果想要获取地理位置详细描述信息需要开发者通过经纬度直接去百度官方定位接口获取。可以参考接口说明：[http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-geocoding](http://lbsyun.baidu.com/index.php?title=webapi/guide/webservice-geocoding)，可以使用MapUtil 地图工具类中的[reverseGeocode (jsonData:Object,callBackFun:Function): void  根据经纬度获取地址详细信息](https://gitdocument.exmobi.cn/sprite-api/maputil.html#ff_3)

