# GaodeMapUtil 高德地图工具类

------------


GaodeMapUtil高德地图工具类，提供坐标转换，离线地图导入，路径计算等功能。

GaodeMapUtil为外置组件。

<h2 id="cid_1">方法</h2>

本节目录：

**坐标转换**

> [converToGcj02(jsonData:Object,callback:Function):void 将其他类型坐标系转换为gcj02国测坐标系](#ff_0)

**地理编码转换**

> [geocode(jsonData:Object,callback:Function):void 根据地质查询高德地图坐标系经纬度](#ff_1)
> 
> [reverseGeocode(jsonData:Object,callback:Function):void 根据经纬度获取地址详细信息](#ff_2)

**Poi搜索**

> [searchInCity(jsonData:Object,callbackFun:Function):void 高德地图市内搜索](#ff_3)
> 
>[searchInBounds(jsonData:Object,callbackFun:Function):void 高德地图矩形区域内搜索](#ff_4)
>
>[searchNearBy(jsonData:Object,callbackFun:Function):void 高德地图圆形区域内搜索]($ff_5)

**调用高德地图进行导航**

> [openGaodeMapNavi(jsonData:Object):void 调起高德地图应用导航页面](#ff_6)

**调用高德地图进行路径规划**

> [openGaodeMapWalkRoute(jsonData:Object):void 调起高德地图应用步行路线规划](#ff_7)
> 
> [openGaodeMapTransitRoute(jsonData:Object):void 调起高德地图应用公交路径规划页面](#ff_8)
> 
> [openGaodeMapDrivingRoute(jsonData:Object):void 调起高德地图应用驾车路径规划页面](#ff_9)

**调用高德地图POI搜索**

> [openGaodeMapPoiNearbySearch(jsonData:Object):void 调起高德地图poi周边检索页面](#ff_10)

**路线面积计算**

> [getDistance(startJson:Object,endJson:Object):number 计算两点间实际地理距离](#ff_11)
> 
> [geteArea(leftTopLatlng:Object,rightBottomLatlng:Object):number 计算地图上矩形区域的面积，单位：平方米](#ff_12)


<span id="ff_0">**converToGcj02(jsonData:Object,callback:Function):void**</span>

<code>将其他类型坐标系转换为gcj02国测坐标系</code>

参数：

jsonData：需要转换的坐标参数定义，json对象：

> type：字符串枚举型，【wgs84，bd09ll，aliyun，google，mapabc，mapbar，sosomap】，必选项
> 
> - wgs84：标准gps坐标系；
> 
> - bd09ll：百度地图坐标系；
> 
> - aliyun：阿里云地图坐标；
> 
> - google：谷歌地图坐标；
> 
> - mapabc：MapABC坐标；
> 
> - mapbar：图吧坐标；
> 
> - sosomap：SoSo地图坐标；
> 
> longitude：需转换坐标经度，数字类型，必选项；
> 
> latitude：需转换坐标纬度，数字类型，必选项；

callback：坐标转换执行回调函数，该函数具有json对象入参，定义如下：

> code：数字枚举型【0，-1】，0：转换成功；-1：转换失败；
> 
> longitude：转换之后的坐标经度，数字类型；
> 
> latitude：转换之后的坐标纬度，数字类型；

返回值：无

<span id="ff_1">**geocode(jsonData:Object,callback:Function):void** </span>

<code>根据地质查询高德地图坐标系经纬度</code>

参数：

jsonData：查询参数，json类型，定义如下：

> city：查询城市名，如北京，南京等，字符串类型，必选项；
> 
> address：查询地址名，字符串类型，必选项；

callback：查询结果回调函数，该函数具有json对象入参，定义如下：

> code：数字枚举型【0，-1】，0：查询成功；-1：查询失败；
> 
> longitude：转换之后的坐标经度，数字类型；
> 
> latitude：转换之后的坐标纬度，数字类型；
> 
> address：查询地址官方描述，字符串类型；

返回值：无


<span id="ff_2">**reverseGeocode(jsonData:Object,callback:Function):void**</span>

<code>根据经纬度获取地址详细信息</code>

参数：

jsonData：查询参数，json类型，定义如下：

> longitude：坐标经度，数字类型；
> 
> latitude：坐标纬度，数字类型；
> 
> coorType：坐标系类型，字符串枚举型，【wgs84，gcj02】

callFunction：查询结果回调函数，该函数具有json对象入参，定义如下：

> code：数字枚举型【0，-1】，0：查询成功；-1：查询失败；
> 
> streetNumber：街道编号，字符串类型；
> 
> address：详细地址，字符串类型；
> 
> district：区县名称，字符串类型；
> 
> city：城市名称，字符串类型；
> 
> longitude：经度，数字类型；
> 
> latitude：纬度，数字类型；
> 
> province：省份名称，字符串类型；
> 
> streetName：街道名称，字符串类型；
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


<span id="ff_3">**searchInCity(jsonData:Object,callbackFun:Function):void **</span>

<code>高德地图市内搜索</code>

参数：

jsonData：搜索参数，json对象，定义如下：

> keyword：搜索关键字，字符串类型，必选项；
> 
> city：需检索城市名，字符串类型，可选项；
> 
> pageNum：查询分页编号，数字，可选项，默认为1；
> 
> pageCapacity：查询每页容量，数字，可选项，默认为10，最多50

callbackFun：查询结果回调，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】。0：查询成功；-1：查询失败；
> 
> totalPoiNum：poi结果总数，数字类型；
> 
> totalpageNum：总分页数，数字类型
> 
> currentPageNum：当前分页编号，数字类型
> 
> currentPageCapacity：当前页返回结果数，数字类型；
> 
> poiInfoList：查询poi结果集，数组类型，数组成员为json对象，定义如下：
> 
> - longitude：坐标经度，数字
> 
> - latitude：坐标纬度，数字
> 
> - name：名称，字符串类型；
> 
> - uid：poi唯一标识
> 
> - address：地址信息，字符串类型；
> 
> - city：所在城市，字符串类型；
> 
> - phone：电话，字符串类型
> 
> - postCode：邮编，字符串类型；
> 
> suggestCityList：城市列表信息结果，数组类型，数组成员为json对象，定义如下：
> 
> - city：城市名，字符串类型
> 
> - num：该城市搜索结果属性，数字类型


返回值：无


<span id="ff_4">**searchInBounds(jsonData:Object,callbackFun:Function):void**</span>

<code>高德地图矩形区域内搜索</code>

参数：

jsonData：搜索参数，json对象，定义如下：

> keyword：搜索关键字，字符串类型，必选项；
> 
> northeastLongitude：区域东北角经度，数字，必选项；
> 
> northeastLatitude：区域东北角纬度，数字，必选项；
> 
> southwestLongitude：区域西南角经度，数字，必选项；
> 
> southwestLatitude：区域西南角纬度，数字，必选项；
> 
> pageNum：查询分页编号，数字，可选项，默认为1；
> 
> pageCapacity：查询每页容量，数字，可选项，默认为10，最多50；

callbackFun：查询结果回调，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】。0：查询成功；-1：查询失败；
> 
> totalPoiNum：poi结果总数，数字类型；
> 
> totalPageNum：总分页数，数字类型；
> 
> currentPageNum：当前分页编号，数字类型；
> 
> currentPageCapacity：当前页返回结果数，数字类型；
> 
> poiInfoList：查询poi结果集，数组类型，数组成员为json对象，定义如下：
> 
> - longitude：坐标经度，数字；
> 
> - latitude：坐标纬度，数字；
> 
> - name：名称，字符串类型；
> 
> - uid：poi唯一标识；
> 
> - address：地址信息，字符串类型；
> 
> - city：所在城市，字符串类型；
> 
> - phone：电话，字符串类型；
> 
> - postCode：邮编，字符串类型；
> 
> suggestCityList：城市列表信息结果，数组类型，数组成员为json对象，定义如下：
> 
> - city：城市名，字符串类型；
> 
> - num：该城市搜索结果属性，数字类型

返回值：无


<span id="ff_5">**searchNearBy(jsonData:Object,callbackFun:Function):void **</span>

<code>高德地图圆形区域内搜索</code>

参数：

jsonData：搜索参数，json对象，定义如下：

> keyword：搜索关键字，字符串类型，必选项；
> 
> longitude：区域中心点经度，数字，必选项；
> 
> latitude：区域中心纬度，数字，必选项；
> 
> radius：区域半径，数字，单位：米，必选项；
> 
> pageNum：查询分页编号，数字，可选项，默认为1
> 
> pageCapacity：查询每页容量，数字，可选项，默认为10，最多50

callbackFun：查询结果回调，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字【0，-1】。0：查询成功；-1：查询失败；
> 
> totalPoiNum：poi结果总数，数字类型；
> 
> totalPageNum：总分页数，数字类型；
> 
> currentPageNum：当前分页编号，数字类型；
> 
> currentPageCapacity：当前页返回结果数，数字类型
> 
> poiInfoList：查询poi结果集，数组类型，数组成员为json对象，定义如下：
> 
> - longitude：坐标经度，数字；
> 
> - latitude：坐标纬度，数字；
> 
> - name：名称，字符串类型；
> 
> - uid：poi唯一标识；
> 
> - address：地址信息，字符串类型；
> 
> - city：所在城市，字符串类型；
> 
> - phone：电话，字符串类型；
> 
> - postCode：邮编，字符串类型；
> 
> suggestCityList：城市列表信息结果，数组类型，数组成员为json对象，定义如下：
> 
> - city：城市名，字符串类型；
> 
> - num：该城市搜索结果属性，数字类型


返回值：无

<span id="ff_6">**openGaodeMapNavi(jsonData:Object):void **</span>

<code>调起高德地图应用导航页面</code>

参数：

jsonData：导航参数，json格式，定义如下：

> end：终点信息设置，josn格式，必选项，定义如下：
> 
> - latitude：终点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
> - longitude：终点经度坐标，数字类型，gcj02高德地图坐标系，必选项

返回值：无

注：调用高德地图默认以当前位置作为起点



<span id="ff_7">**openGaodeMapWalkRoute(jsonData:Object):void **</span>

<code>调起高德地图应用步行路线规划</code>

参数：

jsonData：导航参数，json格式，定义如下：

> end：终点信息设置，json格式，必选项，定义如下：
> 
> - from：起点数据，json格式，定义如下：
> 
>  - latitude：起点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - longitude：起点经度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - name：起点名称，字符串类型，必选项；
>  
> - to：终点数据，json格式，定义如下：
> 
>  - latitude：终点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - longitude：终点经度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - name：终点名称，字符串类型，必选项；

返回值：无


<span id="ff_8">**openGaodeMapTransitRoute(jsonData:Object):void **</span>

<code>调起高德地图应用公交路径规划页面</code>

参数：

jsonData：导航参数，json格式，定义如下：

> end：终点信息设置，json格式，必选项，定义如下：
> 
> - from：起点数据，json格式，定义如下：
> 
>  - latitude：起点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - longitude：起点经度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - name：起点名称，字符串类型，必选项；
>  
> - to：终点数据，json格式，定义如下：
> 
>  - latitude：终点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - longitude：终点经度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - name：终点名称，字符串类型，必选项


返回值：无


<span id="ff_9">**openGaodeMapDrivingRoute(jsonData:Object):void **</span>

<code>调起高德地图应用驾车路径规划页面</code>

参数：

jsonData：导航参数，json格式，定义如下：

> end：终点信息设置，json格式，必选项，定义如下：
> 
> - from：起点数据，json格式，定义如下：
> 
>  - latitude：起点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - longitude：起点经度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - name：起点名称，字符串类型，必选项
>  
> - to：终点数据，json格式，定义如下：
> 
>  - latitude：终点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - longitude：终点经度坐标，数字类型，gcj02高德地图坐标系，必选项；
>  
>  - name：终点名称，字符串类型，必选项；


返回值：无



<span id="ff_10">**openGaodeMapPoiNearbySearch(jsonData:Object):void **</span>

<code>调起高德地图poi周边检索页面</code>

参数：

jsonData：参数设置，json格式，定义如下：

> latitude：查询中心点纬度坐标，数字类型，gcj02高德地图坐标系，必选项；
> 
> longitude：查询中心点经度坐标，数字类型，gcj02高德地图坐标系，必选项；
> 
> keyword：查询关键字，字符串类型，必选项；

返回值：无


<span id="ff_11">**getDistance(startJson:Object,endJson:Object):number **</span>

<code>计算两点间实际地理距离</code>

计算两点间实际地理距离并返回，单位为米

参数：

startJson：起点距离，json对象，定义如下：

> longitude：坐标经度，数字类型，必选项；
> 
> latitude：坐标纬度，数字类型，必选项；

endJson：终点距离，json对象，定义如下：

> longitude：坐标经度，数字类型，必选项；
> 
> latitude：坐标纬度，数字类型，必选项；

返回值：两点间实际地理距离，数字类型，单位：米

注：坐标类型为gcj02


<span id="ff_12">**geteArea(leftTopLatlng:Object,rightBottomLatlng:Object):number **</span>

<code>计算地图上矩形区域的面积，单位：平方米</code>

参数:

leftTopLatlng：左上角坐标，json格式，必选项，定义如下：

> longitude：坐标经度，数字类型，必选项；
> 
> latitude：坐标纬度，数字类型，必选项；

rightBottomLatlng：右下角坐标，json格式，必选项，定义如下：

> longitude：坐标经度，数字类型，必选项；
> 
> latitude：坐标纬度，数字类型，必选项；

返回值：地图上矩形区域的面积，单位：平方米

注：坐标类型为gcj02
