# 版本迭代


----------

**Sprite-1.2.0**  
 
**UI组件：  ** 

1：烽火IM组件；   

2：图片预览组件；   

3：加密输入键盘组件；   

4：candleChart蜡烛图BI组件；   

5：combinedchart复合图BI支持蜡烛图；   


**功能组件：   **

1：高德定位组件；   

2：Mob免费短信组件；   

3：websocket组件；   

4：启用系统设置界面相关方法封装；   

5：系统本地通知组件；   

6：指纹识别；   

7：NFC相关；   

8：系统日程功能； 

**功能完善： **  

1：应用加解密支持，即html，uixml，js，css等应用文件支持加解密，同Mbuild工具配合，Mbuild导出应用插件时加密，Sprite支持加载加密文件；   

2：JS service 后台js执行环境；   

3：支持html页面调用并传参；   

4：list组件功能增强，包括：list的section支持自定义；list的section实现折叠效果；list的cell动态修改dom布局；   

5：slider功能增强，增加半屏展示，增加滑动动画样式；   

6：iOS支持控件边框阴影效果；   

7：增加border单独设置支持；   

8：Android的性能持续性优化；   

9: 插件定义完善：iOS支持xcode权限设置及plist设置，如：步数健康类插件；   

10: Mbuild对接完善：增加appversion等及增加基座升级；   

11:text支持设置html文本用于富文本显示；   

12：Http类download方法增加fileName下载文件名设置；  
 
13：text文本组件支持设置长按弹出系统选择菜单；   

14：list完善scrollToPosition方法；   

15：App增加程序启动后第三方调用事件监听；   

16：容联云/烽火IM支持 IM用户头像https获取；   

17：webview require调整；   

18：Native组件增加分享文件功能；   

19：容联云IM增加链接触发及文件下载触发事件；   

20：百度地图添加标注点增加附加参数设置；   

21：dom对象支持通过xml支持添加节点；   

22：App组件增加获取包名/bundleId方法；   

23：textfield及textarea增加删除键监听；    



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




 


