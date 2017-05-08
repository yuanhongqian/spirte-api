# slider组件使用 

----------

slider滑动页布局组件，允许在子视图之间左右翻页的容器。slider容器支持放置box或scroll作为子容器，每一个子容器会被视作一个单独的页，并且会被拉伸填满该容器。  

slider页布局容器一般用于以下几种典型场景：  

> 1：首页中新闻或广告图片的轮播展示；
> 
> 2：应用首次启动时向导界面；
> 
> 3：整个页面布局支持左右滑动翻页切换，类似网易新闻首页效果；
> 
> 4：隔页切换时不使用动画；
> 
> 5：slider支持通过dom对象动态插入删除子容器，完成后通过sliderObj.refresh()刷新；



<h2 id="cid_1">属性</h2>   


**公共属性**  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-api/ggsx.html)，包括：id、style、class；  


**index**  

<code>当前显示页索引</code>    

取值数字，默认为0，支持设置及获取


**direction**  

<code>滚动方向</code> 

取值 [horizontal，vertical]  

> horizontal：横向滚动（默认）；
> 
> vertical：纵向滚动； 


**drag**  

<code>是否允许手动拖动切换</code>  

取值  [true，false]

> true：允许手动拖动切换（默认）；
> 
> false：不允许手动拖动切换；


**loop**  

<code>是否支持循环滑动</code>  

取值 [true，false] 

> true：支持循环；  
> 
> false：不支持循环（默认）；  
 
 
**注：**  循环滑动子容器应不少于3个  


**autoPlay**  

<code>是否自动切换</code>  

取值 [true，false]  

> true：自动切换；
> 
> false：不自动切换（默认）；


**interval**  

<code>自动切换间隔时间</code> 

取值 数字，单位s  ， 默认3s  


**bounces**  

<code>是否支持弹动</code>  

取值 [true，false] 

> true：支持弹动（默认） 
> 
> false：不支持弹动

**注：** 仅iOS支持



<h2 id="cid_2">样式</h2>  

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-api/ggys.html)，包括：  
 
> 尺寸
> 
> 定位 
> 
> 内边距
> 
> 外边距
> 
> 背景
>
> 显影 
> 
> flexbox布局：align-self，flex





<h2 id="cid_3">事件</h2>


**pageSelected**  

<code>页面切换完成后触发</code>  

该事件会多次触发

event事件对象包括：   

> type：事件类型，字符串类型，固定值：pageSelected；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型
 
param：当前被选中的页面下标索引，数字类型

**注：**    

- 该事件在页面loaded初始化完成的时候就会监听一次，以后每次滑动页面都会执行( 如果在animator 里面监听，页面加载时会监听不到 )。

- 该事件不能放在document.refresh()刷新方法之后监听，建议使用时放在开始位置执行。


**pageScrollStateChanged**  
 
该事件会多次触发

<code>页面滑动状态变化时触发</code> 

event时间对象，包括：  

> type：事件类型，字符串类型，固定值：itemClick；
> 
> target：点击item所在的cell对象，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param：滑动状态，数字类型，[0,1,2]  

> 0：切换动画结束；
> 
> 1：手指触发启动拖动；
> 
> 2：手指释放拖动，开始切换动画；

**注：** 正常拖动事件顺序为1->2->0


**pageScroll**  

<code>页间切换时触发（自动切换或手动拖动）</code> 

该事件会多次触发

event时间对象，包括：  

> type：事件类型，字符串类型，固定值：itemClick；
> 
> target：点击item所在的cell对象，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

param：滑动参数，json类型，定义如下：  

> position：当前页面索引，数字类型
> 
> -  页面完成滑动之前，position一直都是当前页面的位置值
> 
> direction：滑动方向，数字类型，[0,1]
> 
> - 0：向左或向上；
> 
> - 1：向右或向下；
> 
> offset：当前页面滑动比例，数字类型
> 
> - 缓慢滑动时，取值范围 [ 0,1]；
> 
> - 快速滑动时，取值范围[0, 滑过页面的个数]



<h2 id="cid_4">js方法</h2>   


<span id="ff_1">**公共方法**</span>  


[事件相关](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_0)，包括：

> [on(messageName:string,callback:Function): void   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_1)   
> 
> [fire(messageName:string,params:Array&lt;any&gt;): void  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_2)   
> 
> [off(messageName:string,callback:Function): void  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_3)  
>  
> [getOn(messageName:string): Array&lt;Function&gt;  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-api/ggff.html#jjxg_4)   

[动画相关](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_1)，包括： 
 
> [startAnimation(jsonData:Object,callback:Function): void  启动UI组件动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_1)   
> 
> [startAnimator(jsonData:Object,callback:Function): void  启动UI组件属性动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_2)   
> 
> [startKeyFrameAnimator(jsonData:Object,callback:Function): void  启动UI组件关键帧动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_3)  
>  
> [ releaseAnimator(): void  结束控件动画](https://gitdocument.exmobi.cn/sprite-api/ggff.html#dhxg_4)   

[尺寸和位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_2)，包括：  

> [getFrame(): Object  获取组件在父容器中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_1)   
> 
> [setFrame(frame:Object): void  设置组件在父容器中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_2)   
> 
> [getCenter(): Object  获取组件中心点在父容器中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_3)  
>
> [getAbsoluteFrame(): Object  获取组件在绘制窗口中的位置](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cchwz_4)   


[普通Dom节点操作](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_3)，包括：  

> [getParent(): IElement  获取父节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_1)   
> 
> [getNext(): IElement  获取同级下一个节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_2)   
> 
> [getPrevious(): IElement  获取同级前一个节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_3)  
> 
> [remove(): void  从父容器中移除自身](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_4)  
> 
 
> [setAttr(attrName:string,attrValue:string): void  设置节点属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_6)   
>
> [getAttr(attrName:string):string  获取节点属性值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_7) 
>
> [getAttrs(): Object  获取节点所有属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_8) 
>
> [removeAttr(attrName:string): void  移除节点属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_9) 
>
> [hasAttr(attrName:string): boolean  节点是否具有该属性](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_10) 
> 
> [setStyle(styleName:string,styleValue:string): void  设置节点样式值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_13)  
>
> [getStyle(styleName:string):string  获取节点样式值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_14)   
>
> [clearStyle(styleName:string): void  移除节点样式值](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_15)    
>
> [setClassStyle(className:string,domobj:IElement): void   设置节点对应Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.htm#ptdom_16) 
>  
> [getClassStyle(): string  获取节点已设置Class样式](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_17)  
>  
> [getTag(): string  获取UI组件类型](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_18)  
>  
> [getId(): string  获取UI组件Id标识](https://gitdocument.exmobi.cn/sprite-api/ggff.html#ptdom_19) 

[容器类Dom节点操作](https://gitdocument.exmobi.cn/sprite-api/ggff.html#cid_4)：包括：

> [getElement(id:string): IElement  根据Id获取容器内UI控件对象](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_1)   
> 
> [getElements(rule:string): Array&lt;IElement&gt;  根据特定规则获取容器内UI控件对象集](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_2)   
> 
> [getChildren():Array&lt;IElement&gt;  容器获取子节点集](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_3)  
>  
> [getFirstChild(): IElement  容器获取首子节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_4) 
>  
> [getLastChild(): IElement  容器获取尾节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_5) 
>  
> [appendChild(Obj:IElement): void  容器添加子节点至尾部](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_6) 
>  
> [insertBefore(domObj:IElement,beforeDomObj:IElement): void  容器在指定的已有的子节点之前插入新节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_7) 
>  
> [insertAfter (domObj:IElement,afterDomObj:IElement): void  容器在指定的已有的子节点之后插入新节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_8) 
>  
> [replaceChild(newDomObj:IElement,oldDomObj:IElement): void  容器替换子节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_9) 
>  
> [clear(): void  清空容器内所有子节点](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_10) 
>  
> [getInnerHTML(): string  动态获取容器内子节点xml](https://gitdocument.exmobi.cn/sprite-api/ggff.html#rqczdom_11)  


**refresh(index:number): void**  

<code>刷新slider指定item区域</code>

参数：  

index：需要刷新item区域索引，数字类型，可选参数；  

返回值：无  

**注：**

- 该方法主要用于两种场景，代替document.refresh()获得更好的刷新效果

- 1：当Element对象属性或者CSS更新完毕后，调用该函数刷新至系统UI界面；

- 2：添加或删除子容器后，调用该函数刷新至系统UI界面；





<h2 id="cid_5">示例</h2>  


示例代码1，测试slider事件和方法，参考演示应用示例：apps\yuanhongqian\spriteui\slider+uievent.uixml，代码中用到了官方封装的模板titlebar，模板的使用可参考[https://gitdocument.exmobi.cn/sprite-official-ui/index.html](https://gitdocument.exmobi.cn/sprite-official-ui/index.html "https://gitdocument.exmobi.cn/sprite-official-ui/index.html") 

```html
<page>
    <script>
        <![CDATA[
        var window = require("Window");
        var document = require("Document");
        var Time = require("Time");
        var console = require("Console");
        require("buttonUI");
        require("titlebarUI");


        var btnWidth = 0;
        var testbtn = null;
        var testbtn2 = null;
        var screenW = window.getScreenWidth();
        var ui = require("UI");
        window.on("loaded", function () {

            testbtn = document.getElement("testbtn");
            testbtn2 = document.getElement("testbtn2");
            btnWidth = screenW / 3;
            testbtn.setStyle("width", btnWidth);
            testbtn2.setStyle("width", btnWidth);
            document.refresh();

            var slider = document.getElement("slider1");
            var slider2 = document.getElement("slider2");
            var btn = document.getElement("btn");
            var page1 = document.getElement("page1");
            var page2 = document.getElement("page2");
            var page3 = document.getElement("page3");
            var text = document.getElement("text");
            slider.on("pageSelected", function (e, param) {
                text.setText("第" + param + "页");
                if (param == 0) {
                    page1.setStyle("opacity", 1);
                    page2.setStyle("opacity", 0.5);
                    page3.setStyle("opacity", 0.5);
                } else if (param == 1) {
                    page1.setStyle("opacity", 0.5);
                    page2.setStyle("opacity", 1);
                    page3.setStyle("opacity", 0.5);
                } else if (param == 2) {
                    page1.setStyle("opacity", 0.5);
                    page2.setStyle("opacity", 0.5);
                    page3.setStyle("opacity", 1);
                }

            });

            slider.on("pageScrollStateChanged", function (e, param) {
                console.log("pageScrollStateChanged:" + param);

            });

            slider.on("pageScroll", function (e, json) {
                var position = json.position;
                var direction = json.direction;
                var offset = json.offset;

                var frame = testbtn.getFrame();
                if (direction == 0) {
                    if (position == 2) {
                        frame.x = position * btnWidth - offset * (btnWidth * 2);
                        testbtn.setFrame(frame);
                    } else {
                        frame.x = position * btnWidth + offset * btnWidth;
                        testbtn.setFrame(frame);
                    }

                } else {
                    if (position == 0) {
                        frame.x = position * btnWidth + offset * (btnWidth * 2);
                        testbtn.setFrame(frame);
                    } else {
                        frame.x = position * btnWidth - offset * btnWidth;
                        testbtn.setFrame(frame);
                    }
                }

            });

            slider2.on("pageScroll", function (e, json) {
                var position = json.position;
                var direction = json.direction;
                var offset = json.offset;
                var red = 255;
                var green = 255;
                var blue = 255;
                var frame = testbtn2.getFrame();
                if (direction == 0) {
                    frame.x = position * btnWidth + offset * btnWidth;
                    testbtn2.setFrame(frame);
                    if (position == 0) {
                        red = 255;
                        green = 0;
                        blue = 0;
                        red = 255 * (1 - offset);
                        green = 255 * offset;
                    } else if (position == 1) {
                        red = 0;
                        green = 255;
                        blue = 0;
                        green = 255 * (1 - offset);
                        blue = 255 * offset;
                    } else {
                        red = 0;
                        green = 0;
                        blue = 255;
                    }

                    var color = "rgb(" + red + "," + green + "," + blue + ")";
                    testbtn2.setStyle("background-color", color);

                } else {
                    frame.x = position * btnWidth - offset * btnWidth;
                    testbtn2.setFrame(frame);

                    if (position == 2) {
                        red = 0;
                        green = 0;
                        blue = 255;
                        blue = 255 * (1 - offset);
                        green = 255 * offset;
                    } else if (position == 1) {
                        red = 0;
                        green = 255;
                        blue = 0;
                        green = 255 * (1 - offset);
                        red = 255 * offset;
                    } else {
                        red = 255;
                        green = 0;
                        blue = 0;
                    }
                    var color = "rgb(" + red + "," + green + "," + blue + ")";
                    testbtn2.setStyle("background-color", color);
                }

            });

            btn.on("click", function (e, param) {
                slider.setAttr("index", 2);
                slider2.setAttr("index", 2);
            });

            var title = document.getElement("title");
            title.on("left_btn_click", function (e) {
                var json = {};
                json.data = {};
                json.data.text = "动画页面关闭";
                json.animation = "slide_b2t";
                window.close(json);

            });
            //tt.alert("123");
        });

        function alert(msg) {
            var json = {};
            json.title = "提示";
            json.content = msg;
            json.buttonText = "确定";
            ui.alert(json);
        }
        function closePage() {
            var json = {};
            json.data = {};
            json.data.text = "页面关闭";
            window.close(json);
        }
    ]]>
    </script>
    <style>
        @import url(res:spritetest/css/import.css);
        slider {
            width: fill_screen;
            flex: 1;
            background-color: black;
        }
        
        text {
            margin: 5 5 5 5;
            color: red;
        }
        
        .box {
            background-color: rgba(0, 0, 0, 0.5);
            height: 25;
            bottom: 0;
            left: 0;
            right: 0;
            position: absolute;
            justify-content: flex-start;
            flex-wrap: nowrap;
            flex-direction: row;
            align-items: center;
        }
        
        .pagebox {
            width: 6;
            height: 6;
            border-radius: 3;
            background-color: #FFFFFF;
            margin: 0 0 0 5;
        }
        
        .textbox {
            font-size: 15;
            color: #ffffff;
        }
    </style>
    <ui>
        <box class="rootBox">
            <titlebar title="slider测试" id="title" ltext="返回"  style="height: 66;padding:20 0 0 0"/>
            <button value="点击测试" id="btn" />
            <box style="flex-direction:row;flex-wrap:nowrap;background-color:red">
                <button style="background-color:blue;height:50;width:50" id="testbtn" />
            </box>
            <box style="height:200">
                <slider loop="true" style="flex:0;height:200" id="slider1" direction="ertical" index="1">
                    <box>
                        <image src="res:spritetest/image/1.jpg" style="flex:1;scaleType:cover" />
                    </box>
                    <box>
                        <image src="res:spritetest/image/2.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                    </box>
                    <box>
                        <image src="res:spritetest/image/3.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                    </box>
                </slider>
                <box class="box">
                    <text id="text" class="textbox">第一页</text>
                    <box style="flex:1" />
                    <box id="page1" class="pagebox" />
                    <box id="page2" class="pagebox" />
                    <box id="page3" class="pagebox" style="margin:0 5 0 5" />
                </box>
            </box>
            <box style="flex-direction:row;flex-wrap:nowrap;background-color:yellow">
                <button style="background-color:red;height:50;width:50" id="testbtn2" />
            </box>
            <slider loop="false" style="flex:0;height:200" id="slider2" direction="ertical" index="1">
                <box>
                    <image src="res:spritetest/image/1.jpg" style="flex:1;scaleType:cover" />
                </box>
                <box>
                    <image src="res:spritetest/image/2.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                </box>
                <box>
                    <image src="res:spritetest/image/3.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                </box>
            </slider>
        </box>
    </ui>
</page>
```

代码效果：

<img src="image/slider_1.gif" width="250"/>  
 
示例代码2，测试grid基本布局，示例代码参考apps\yuanhongqian\sprite_xiaoguo\grid.uixml

```html

<page>
    <script>
        <![CDATA[
        var window = require("Window");
        var document = require("Document");
        var ui = require("UI");

        var console = require("Console");
        var myappjs = require("myapp");
        var app = require("App");
        window.on("loaded", function () {

            var screenWidth = window.getScreenWidth();
            //关闭页面
            var imageid = document.getElement("imageid");
            imageid.on("click", function (e) {
                var json = {};
                window.close(json);
            });
            var slider1 = document.getElement("slider1");
            var slider2 = document.getElement("slider2");
            var markbox1 = document.getElement("markbox1");
            var markbox2 = document.getElement("markbox2");
            var markbox3 = document.getElement("markbox3");
            var markbox2_1 = document.getElement("markbox2_1");
            var markbox2_2 = document.getElement("markbox2_2");
            var markbox2_3 = document.getElement("markbox2_3");
            var text = document.getElement("text");
            slider1.on("pageSelected", function (e, param) {
                console.log("第" + param + "页");
                text.setText("第" + param + "页");
                if (param == 0) {
                    markbox1.setStyle("opacity", 1);
                    markbox2.setStyle("opacity", 0.5);
                    markbox3.setStyle("opacity", 0.5);
                }
                else if (param == 1) {
                    markbox1.setStyle("opacity", 0.5);
                    markbox2.setStyle("opacity", 1);
                    markbox3.setStyle("opacity", 0.5);
                }
                else if (param == 2) {
                    markbox1.setStyle("opacity", 0.5);
                    markbox2.setStyle("opacity", 0.5);
                    markbox3.setStyle("opacity", 1);
                }
                document.refresh();

            });

            slider2.on("pageSelected", function (e, param) {

                if (param == 0) {
                    markbox2_1.setStyle("opacity", 1);
                    markbox2_2.setStyle("opacity", 0.5);
                    markbox2_3.setStyle("opacity", 0.5);
                }
                else if (param == 1) {
                    markbox2_1.setStyle("opacity", 0.5);
                    markbox2_2.setStyle("opacity", 1);
                    markbox2_3.setStyle("opacity", 0.5);
                }
                else if (param == 2) {
                    markbox2_1.setStyle("opacity", 0.5);
                    markbox2_2.setStyle("opacity", 0.5);
                    markbox2_3.setStyle("opacity", 1);
                }

            });
        });

        app.on("orientation", function (e, orientation) {
            var screenWidth = window.getScreenWidth();

        });	
    ]]>
    </script>
    <style>
        @import url("spriteLayout");
        @import url("spriteColor");
        text {
            text-overflow: ellipsis;
            singleline: true;
        }
    </style>
    <ui>
        <box class="bg-white full" id="box">
            <box class="titlebar-hasstatus" style="background-color:#549FF7;">

                <text class="titlebar-text white">滑动栏效果</text>
                <box id="imageid" class="titlebar-lcaption">
                    <image class="margin8 titlebar-image" src="res:yuanhongqian/image/back.png" />
                </box>
                <box class="titlebar-rcaption">
                    <text class="margin8 text-center peter-river"></text>
                </box>
            </box>
            <line />
            <scroll class="flex1" style="background-color:#ececec">
                <box style="height:200">
                    <slider index="1" loop="true" style="flex:1;height:200" id="slider1">
                        <box>
                            <image src="res:yuanhongqian/image/1.jpg" style="flex:1;scaleType:cover" />
                        </box>
                        <box>
                            <image src="res:yuanhongqian/image/2.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                        </box>
                        <box>
                            <image src="res:yuanhongqian/image/3.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                        </box>
                    </slider>
                    <box class="slider-bottom-mark-box">
                        <text id="text" class="slider-textbox flex1">2222222</text>

                        <box id="markbox1" class="markbox" />
                        <box id="markbox2" class="markbox" />
                        <box id="markbox3" class="markbox" />
                    </box>
                </box>
                <box style="height:10;" />
                <line style="line-size:0.5" />
                <box style="height:200">
                    <slider autoPlay="true" interval="2" loop="true" style="flex:0;height:200" id="slider2">
                        <box>
                            <image src="res:yuanhongqian/image/1.jpg" style="flex:1;scaleType:cover" />
                        </box>
                        <box>
                            <image src="res:yuanhongqian/image/2.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                        </box>
                        <box>
                            <image src="res:yuanhongqian/image/3.jpg" style="flex:1;width:fill_screen;scaleType:cover" />
                        </box>
                    </slider>
                    <box class="slider-bottom-notext-mark-box">

                        <box id="markbox2_1" class="markbox" />
                        <box id="markbox2_2" class="markbox" />
                        <box id="markbox2_3" class="markbox" />
                    </box>
                </box>
                <box style="height:10;" />
                <line style="line-size:0.5" />
                <box class="row-flex-center margin4" style="background-color:#ffffff;border-color:#dddddd;border-width:1">
                    <image src="res:yuanhongqian/image/today_hot_icon.png" style="width:60;height:70;scaleType:cover" />
                    <slider class="flex1" style="height:70;margin:0 0 0 4" direction="vertical" autoPlay="true" interval="2" loop="true">
                        <box>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">古巴民众街头排队悼念卡斯特罗</text>
                            </box>
                            <line/>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">美国俄州大学发生枪杀案 9人受伤</text>
                            </box>
                            <line/>

                        </box>
                        <box>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">上厕所没带纸 灵机一动让外卖小哥送</text>
                            </box>
                            <line/>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">实在是高！ 马伊琍发微博对贤惠姚笛</text>
                            </box>
                            <line/>

                        </box>
                        <box>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">古巴民众街头排队悼念卡斯特罗</text>
                            </box>
                            <line/>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">美国俄州大学发生枪杀案 9人受伤</text>
                            </box>
                            <line/>

                        </box>
                        <box>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">上厕所没带纸 灵机一动让外卖小哥送</text>
                            </box>
                            <line/>
                            <box class="row-flex-center" style="height:35">
                                <text class="flex1 margin4" style="text-align:left">实在是高！ 马伊琍发微博对贤惠姚笛</text>
                            </box>
                            <line/>
                        </box>
                    </slider>
                </box>
            </scroll>
        </box>
    </ui>
</page>

```

<img src="image/slider_2.gif" width="250"/>  



