# 版本迭代



----------

**Sprite-1.0.2**  

1：新增极光推送

2：新增容联云IM

3：新增BI饼状图

4：新增BI折线图

5：新增BI柱状图

6：新增BI符合图

7：入口require.config文件调整，将该配置项设置为独立的设置文件，并在app.json中进行设置

8：require函数调整，require("组件路径或标识") 调整为 require("组件路径或标识","组件Tag名")，第二个参数为可选项，若不设置则以组件文件名为Tag名，若设置则以该设置项为Tag名。

9：新增手势锁屏组件

10：新增一键分享，实现WeiXin，Qq，WeiBo分享功能

11：百度地图完善：
> BaiduMap UI组件功能继续完善，包括：
>1：聚合mark点功能支持；
>2：点击Mark弹出Pop窗口功能支持；
>3: 增加MapUtil调用百度地图App相关能力支持；
>4: 支持比例尺，logo等特定标注点自定义位置设置；
>5：mark点支持图片+文字展现模式，支持左右，右左，上下，下上四种布局，支持mark点偏移量设置；
>6：地图定位点增加heading普通带箭头模式，去除enableDirection方向设置；
>7：增加地图拖动过程中实时状态改变监听事件； 

12：Mbuilder日志输出格式统一

13：新增群组联动选择

14：新增系统分享组件

15：webview桥接功能支持

16：字体库EDN打包

----------

**Sprite-1.0.1**  

ChangeLog： 

1：新增调试首页界面增加二维码扫码功能，便于通过二维码快速获取Mbuilder地址； 

2：新增Js报错提示，定位至出错文件及行号，通过提示框及错误日志提示； 

3：新增App组件getVersion()获取应用版本号及getSdkVersion()获取SDK版本号； 

4：新增Contact组件selectSystemContact(),selectSystemContactProperty()调用系统通讯录界面并选择返回； 

5：baimap百度地图组件方法调整，setCenter -> setMapCenter， getCenter->getMapCenter； 

6：require.config调整为单独配置文件，并在应用入口app.json中进行设置； 

7：Mbuilder输出日志格式统一，普通日志优化输出格式并支持dom对象详细信息打印，系统日志增加开窗及Js报错输出； 

8：优化Android执行效率，开窗及刷新速度较1.0.0版本有较大提升； 

9：优化Android输入法弹出时窗口处理，开窗时增加resizeMode【pan,resize】用于不同场景； 

10：近期外部试用反馈问题修复；




 


