# CSS外部导入

---------



<h2 id="cid_1">基础使用</h2>

使用&lt;style&gt;标签中添加，@import url("CSS路径")，放置于sytle标签内顶部位置，导入外部CSS样式表文件，只支持加载本地css文件，传入路径为基于应用文件夹相对路径。

示例：
```html
//页面中引入css/login.css,css/common.css布局文件
<page>
	<ui>
		<box>
			<text style="font-size:32;">烽火星空</text>
			<text class="large">Sprite Team</text>
		</box>
	</ui>
	<style>
		@import url("res:css/login.css");
		@import url("res:css/common.css");
		.large{font-size:64;}
	</style>
</page>
```

<h2 id="cid_2">require.js配置</h2>

通过应用入口app.json指定require.json来配置css文件加载路径（@import 加载路径），支持应用级配置


require.json示例

```json
{
	"jsPaths":{
		"CK":"res:testSprite/agile/ck.js"
	},
	"cssPaths":{
		"MVVM":"agile/css/mvvm.css",
	},
	"componentPaths":{
		"FHBUTTON":"res:testSprite/temp/fhbutton.component"
	}
}

//页面中使用

@import url("MVVM");
```

<h2 id="cid_3">优先级</h2>

@import 支持3种路径的的写法：res:开始的绝对的路径，require.config里配置的标识，当前文件的相对路径。

Sprite处理逻辑为：@import url("xxx")不是绝对路径，则进行require.config里配置的标识匹配，若无法匹配则再进行相对路径处理。
