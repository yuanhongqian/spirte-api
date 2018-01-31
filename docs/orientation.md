# 横竖屏切换


<h2 id="cid_1">应用级横竖屏</h2>

通过app.json应用配置文件设置，如下所示

**app.json文件定义**

```json
{
	"homeJs":"res:page/home.js",
	"orientation":"portrait"
}
```

**orientation**

<code>应用默认横竖屏设置</code>

字符串枚举型，【portrait，landscape，device】

> portrait：竖屏（默认）
> 
> landscape：横屏
> 
> device：支持横竖屏切换


<h2 id="cid_2">页面级横竖屏</h2>

Window组件调用open(jsonData),openData(jsonData)时，通过orientation参数可设置页面单独横竖屏配置。

orientation：当前页面横竖屏设置，字符串枚举型，可选项，若不设置则采用app.json应用配置文件中统一设置，【portrait，landscape，device】
> portrait：竖屏；
> 
> landscape：横屏；
> 
> device：支持横竖屏；
