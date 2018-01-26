# JS外部导入

------------


Sprite页面逻辑代码一般是在.uixml文件中&lt;script&gt; 中编写，实际项目中需要封装javascript代码作为函数模块，这样可再不同项目或页面中方便使用。

Sprite采用CommonJS规范，模块中通过module.exports实现函数声明，通过require("模块标识")来加载外部JS模块。


<h2 id="cid_1">定义JS函数</h2>

JS模块文件后缀为.js，JS模块中通过module.exports实现函数声明，示例如下：

示例：文件名calculate.js

````javascript
//函数定义

function sumValue(t1,t2){
	return t1+t2;
}

//函数声明
module.exports.sum = sumValue;
````
<h2 id="cid_2">使用JS函数</h2>

通过require("模块标识")来加载外部JS模块，只支持加载本地js文件，传入模块标识为js文件路径，支持绝对路径及相对路径。

示例：文件名test.js


	//调用calculate.js模块sum函数
	var calculate = require("res:js/calculate.js");

	var result = calculate.sum(8,12);



<h2 id="cid_3">require.js配置</h2>

通过应用入口app.json指定require.json来配置js文件加载路径，支持应用级配置。

require.json示例
		
     {
		"jsPaths":{
			"CK":"res:testSprite/agile/ck.js"
	 	},
	    "cssPaths":{
			"MVVM":"agile/css/mvvm.css"

	 	},
	    "componentPaths":{
			"FHBUTTON":"res:testSprite/temp/fhbutton.component"
		}
	}
	//页面中使用
	require(CK);



<h2 id="cid_4">优先级</h2>

require("xx")支持3中路径的写法：res:开始的绝对的路径，require.config里配置的标识，当前文件的相对路径。

Sprite处理逻辑为：若require("xx")不是绝对路径，则进行require.config里配置的标识匹配，若无法匹配则再进行相对路径处理。