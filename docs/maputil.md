# MapUtil 地图工具类

----------

MapUtil地图工具类，提供提供坐标转换，离线地图导入，路径计算等功能。

该工具类和百度地图绑定，开发者自行打包使用时，需要去百度地图官网申请对于的key值。

使用时需要在js中引入 ：

```javascript
var maputil = require("MapUtil"); 
```

**注：** 该组件为外置功能组件，打包需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录： 

> **坐标转换**
> 
>[ convertToBd09ll(srcJson:Object,callFunction:Function): void   将gcj02/wgs84转换为bd09ll百度坐标系 ](#ff_0)
> 
> [convertToGcj02(jsonData:Object,callBackFun:Function): void  将bd09ll/wgs84转换为gcj02国测坐标系 ](#ff_1)


>**地理编码转换**
> 
> [geocode(jsonData:Object,callBackFun:Function): void    根据地址查询百度地图坐标系经纬度 ](#ff_2)
> 
> [reverseGeocode (jsonData:Object,callBackFun:Function): void  根据经纬度获取地址详细信息](#ff_3)

>
>**Poi搜索**
> 
> [searchInCity(jsonData:Object,callFunction:Function): void  百度地图市内搜索](#ff_4)
> 
> [searchInBounds(jsonData:Object,callFunction:Function): void  百度地图矩形区域内搜索](#ff_5)
> 
> [searchNearBy(jsonData:Object,callFunction:Function): void  百度地图圆形区域内搜索](#ff_6)
>
>**其他**
>
> [getDistance(startJson:Object,endJson:Object): number  计算两点间实际地理距离](#ff_7)





<span id="ff_0">**convertToBd09ll(srcJson:Object,callFunction:Function): void**</span>  

<code>将gcj02/wgs84转换为bd09ll百度坐标系</code>  

缩放图片并保存到目标文件，结果通过回调函数返回   

参数：  

jsonData，需要转换的坐标参数定义，Json对象： 

> type：字符串枚举型，[gcj02，wgs84]，必选项
> 
> - gcj02：国测坐标系
> 
> - wgs84：标准gps坐标系 
> 
> longitude：需转换坐标经度，数字类型，必选项；
> 
> latitude：需转换坐标纬度，数字类型，必选项；

callFunction，坐标转换执行回调函数，该函数具有Json对象入参，定义如下：

> code：数字枚举型[0，-1]
> 
> - 0：转换成功
> 
> - -1：转换失败
> 
> longitude：转换之后的坐标经度，数字类型
> 
> latitude：转换之后的坐标纬度，数字类型

返回值：无





<span id="ff_1">**convertToGcj02(jsonData:Object,callBackFun:Function): void**</span>  

<code>将bd09ll/wgs84转换为gcj02国测坐标系</code>   

参数：

jsonData，需要转换的坐标参数定义，Json对象：

> type：字符串枚举型，[wgs84, bd09ll]，必选项
> 
> - wgs84：标准gps坐标系
> 
> - bd09ll：百度地图坐标系
> 
> longitude：需转换坐标经度，数字类型，必选项
> 
> latitude：需转换坐标纬度，数字类型，必选项

callFunction，坐标转换执行回调函数，该函数具有Json对象入参，定义如下：

> code：数字枚举型[0，-1]
> 
> - 0：转换成功
> 
> - -1：转换失败
> 
> longitude：转换之后的坐标经度，数字类型
> 
> latitude：转换之后的坐标纬度，数字类型


返回值：无

**注：** 调用该函数请保持网络可用









<span id="ff_2">**geocode(jsonData:Object,callBackFun:Function): void**</span>  

<code>根据地址查询百度地图坐标系经纬度</code>  


参数：  

jsonData：查询参数，json类型，定义如下：
 
> city：查询城市名，如北京，南京等，字符串类型，必选项；
> 
> address：查询地址名，字符串类型，必选项；

callBackFun：查询结果回调函数，该函数具有Json对象入参，定义如下：

> code：数字枚举型[0，-1]
> 
> - 0：查询成功；
> 
> - -1：查询失败；
> 
> longitude：转换之后的坐标经度，数字类型
> 
> latitude：转换之后的坐标纬度，数字类型
> 
> address：查询地址官方描述，字符串类型

返回值：无


<span id="ff_3">**reverseGeocode (jsonData:Object,callBackFun:Function): void**</span>  

<code>根据经纬度获取地址详细信息</code> 

参数：  

jsonData：查询参数，json类型，定义如下 ：

> longitude，坐标经度，数字类型，bd09ll坐标系 
> 
> latitude，坐标纬度，数字类型，bd09ll坐标系

callBackFun：查询结果回调函数，该函数具有Json对象入参，定义如下：

> code：数字枚举型[0，-1]
> 
> - 0：查询成功；
> 
> - -1：查询失败；
> 
> streetNumber，街道编号，字符串类型；
> 
> address，详细地址，字符串类型；
> 
> district，区县名称，字符串类型；
> 
> city，城市名称，字符串类型；
> 
> longitude，经度，数字类型；
> 
> latitude 纬度，数字类型；
> 
> province：省份名称，字符串类型；
> 
> streetName街道名称，字符串类型；
> 
> poiList：周边地址信息列表，数组，数组中每项均为json字段，定义如下：
> 
> - name：名称，字符串类型；
> 
> - address：详细地址，字符串类型；
> 
> - latitude：纬度，数字类型，bd09ll坐标系；
> 
> - longitude：经度，数字类型，bd09ll坐标系；

返回值：无


<span id="ff_4">**searchInCity(jsonData:Object,callFunction:Function): void**</span>  

<code>百度地图市内搜索</code>  


参数： 

jsonData：搜索参数，Json对象，定义如下：  

> keyword：搜索关键字，字符串类型，必选项；
> 
> city：需检索城市名，字符串类型，可选项；
> 
> pageNum：查询分页编号，数字，可选项，默认为0
> 
> pageCapacity：查询每页容联，数字，可选项，默认为10，最多50

callFunction：查询结果回调，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> -  0：查询成功；
> 
> - -1：查询失败
> 
> totalPoiNum：poi结果总数，数字类型
> 
> totalPageNum：总分页数，数字类型
> 
> currentPageNum：当前分页编号，数字类型
> 
> currentPageCapacity：当前页返回结果数，数字类型
> 
> poiInfoList：查询poi结果集，数组类型，数组成员为Json对象，定义如下：
> 
> - longitude：坐标经度，数字
> 
> - latitude：坐标纬度，数字
> 
> - name：名称，字符串类型
> 
> - uid：poi唯一标识
> 
> - type：poi类型，0：普通点，1：公交站，2：公交线路，3：地铁站，4：地铁线路
> 
> - address：地址信息，字符串类型
> 
> - city：所在城市，字符串类型
> 
> - phone：电话，字符串类型
> 
> - postCode：邮编，字符串类型
> 
>suggestCityList：城市列表信息结果，数组类型，数组成员为Json对象，定义如下：
>  
> - city：城市名，字符串类型
> 
> - num：该城市搜索结果属性，数字类型
> 
> hasAddressInfo：是否包含门址类数据，bool型
> 
> addressInfoList：门址类数据，数组类型，数组成员为Json对象，定义如下：
> 
> - longitude：坐标经度，数字
> 
> - latitude：坐标纬度，数字
> 
> - name：名称，字符串类型
> 
> - address：门址信息，字符串类型
        
返回值：无


<span id="ff_5">**searchInBounds(jsonData:Object,callFunction:Function): void**</span>  

<code>百度地图矩形区域内搜索</code>   

参数： 

jsonData：搜索参数，Json对象，定义如下：  

> keyword：搜索关键字，字符串类型，必选项；
> 
> northeastLongitude：区域东北角经度，数字，必选项
> 
> northeastLatitude：区域东北角纬度，数字，必选项
> 
> southwestLongitude：区域西南角经度，数字，必选项
> 
> southwestLatitude：区域西南角纬度，数字，必选项
> 
> pageNum：查询分页编号，数字，可选项，默认为0
> 
> pageCapacity：查询每页容联，数字，可选项，默认为10，最多50

callFunction：查询结果回调，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> -  0：查询成功
> 
> - -1：查询失败
> 
> totalPoiNum：poi结果总数，数字类型
> 
> totalPageNum：总分页数，数字类型
> 
> currentPageNum：当前分页编号，数字类型
> 
> currentPageCapacity：当前页返回结果数，数字类型
> 
> poiInfoList：查询poi结果集，数组类型，数组成员为Json对象，定义如下：
> 
> - longitude：坐标经度，数字
> 
> - latitude：坐标纬度，数字
> 
> - name：名称，字符串类型
> 
> - uid：poi唯一标识
> 
> - type：poi类型，0：普通点，1：公交站，2：公交线路，3：地铁站，4：地铁线路
> 
> - address：地址信息，字符串类型
> 
> - city：所在城市，字符串类型
> 
> - phone：电话，字符串类型
> 
> - postCode：邮编，字符串类型
> 
> suggestCityList：城市列表信息结果，数组类型，数组成员为Json对象，定义如下：
> 
> - city：城市名，字符串类型
> 
> - num：该城市搜索结果属性，数字类型
> 
>  hasAddressInfo：是否包含门址类数据，bool型
>  
>  addressInfoList：门址类数据，数组类型，数组成员为Json对象，定义如下：
>  
> - longitude：坐标经度，数字
> 
> - latitude：坐标纬度，数字
> 
> - name：名称，字符串类型
> 
> - address：门址信息，字符串类型
        
返回值：无


<span id="ff_6">**searchNearBy(jsonData:Object,callFunction:Function): void**</span>  

<code>百度地图圆形区域内搜索</code> 


参数：
jsonData：搜索参数，Json对象，定义如下：

> keyword：搜索关键字，字符串类型，必选项
> 
> longitude：区域中心点经度，数字，必选项
> 
> latitude：区域中心点纬度，数字，必选项
> 
> radius：区域半径，数字，单位：米，必须项
> 
> pageNum：查询分页编号，数字，可选项，默认为0
> 
> pageCapacity：查询每页容联，数字，可选项，默认为10，最多50

callFunction：查询结果回调，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> -  0：查询成功
> 
> - -1：查询失败
> 
> totalPoiNum：poi结果总数，数字类型
> 
> totalPageNum：总分页数，数字类型
> 
> currentPageNum：当前分页编号，数字类型
> 
> currentPageCapacity：当前页返回结果数，数字类型
> 
> poiInfoList：查询poi结果集，数组类型，数组成员为Json对象，定义如下：
> 
> - longitude：坐标经度，数字
> 
> - latitude：坐标纬度，数字
> 
> - name：名称，字符串类型
> 
> - uid：poi唯一标识
> 
> - type：poi类型，0：普通点，1：公交站，2：公交线路，3：地铁站，4：地铁线路
> 
> - address：地址信息，字符串类型
> 
> - city：所在城市，字符串类型
> 
> - phone：电话，字符串类型
> 
> - postCode：邮编，字符串类型
> 
> suggestCityList：城市列表信息结果，数组类型，数组成员为Json对象，定义如下：
> 
> - city：城市名，字符串类型
> 
> - num：该城市搜索结果属性，数字类型
> 
> hasAddressInfo：是否包含门址类数据，bool型
>  
> addressInfoList：门址类数据，数组类型，数组成员为Json对象，定义如下：
>  
> - longitude：坐标经度，数字
> 
> - latitude：坐标纬度，数字
> 
> - name：名称，字符串类型
> 
> - address：门址信息，字符串类型
  
返回值：无


<span id="ff_7">**getDistance(startJson:Object,endJson:Object): number**</span>  

<code>计算两点间实际地理距离并返回</code>

计算两点间实际地理距离并返回，单位为米 


参数：

startJson：起点距离，Json对象，定义如下：

> longitude，坐标经度，数字类型，必选项；
> 
> latitude，坐标纬度，数字类型，必选项；

endJson：终点距离，Json对象，定义如下：

> longitude，坐标经度，数字类型，必选项；
> 
> latitude，坐标纬度，数字类型，必选项；

返回值：两点间实际地理距离，数字类型，单位：米
