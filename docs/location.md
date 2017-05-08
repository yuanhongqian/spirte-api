#  Location 定位操作类

----------
Location 定位操作类，基于手机自身定位能力提供获取GPS、网络定位经纬度功能。

使用时需要在js中引入 ：

```javascript
var location = require("Location"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

<span id="ff_0">**start(jsonData:Object,callFunction:Function): void**</span>  

<code>启动系统单次定位</code>  

参数： 

jsonData：Json对象，定义如下：  

> mode：定位模式，字符串枚举型，[gps,gpsFirst,network,networkFirst]，可选项，仅对Android生效
> 
> -   gps：GPS定位（默认）
> 
> -   gpsFirst：GPS定位优先
> 
> -   network：网络定位
> 
> -   networkFirst：网络定位优先
> 
> accuracy：定位精度，字符串枚举型，可选项，[BestForNavigation，Best，NearestTenMeters，HundredMeters，Kilometer，ThreeKilometers]，仅对iOS生效
> 
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
> timeOut：定位超时时间，数字，单位：秒，可选项，默认值60

callFunction：定位结果回调，参数为Json对象定义如下：

>  code：回应状态码，数字
>  
> -       0：定位成功
> 
> -       -1：定位失败 
> 
> longitude：坐标经度，数字
> 
> latitude：坐标纬度，数字
> 
> address：地址信息，字符串
> 
> accuracy：精度信息，数字 
> 
> speed：速度，数字，单位：m/s，未获取返回-1
> 
> altitude：海拔高度，数字，单位：米
 
返回值：无

**注：**  android的定位精度通过mode类型来确定，ios定位精度通过accuracy来取确定。定位精度越高要求定位的环境就越好，在信号不好或者天气不好的情况下，可能定位会失败。



