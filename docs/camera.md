# Camera 拍照，摄像操作类。

----------

Camera拍照，摄像操作类，用于调用摄像头进行拍照和摄像。


使用时需要在js中引入 ：

```javascript
var camera = require("Camera"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

<span id="ff_0">**start(jsonData:Object,callFunction:Function): void **</span>  

<code>启动系统拍照/摄像界面</code>    


参数：  

jsonData：传入设置参数，Json对象，定义如下：  

> **mode**：拍照模式，字符串枚举型，必选参数，[photo，video]
> 
> -  photo：拍照模式；
> 
> -  video：摄像模式  
> 
> **path**：拍照/摄像生成文件路径（包含文件名），支持res: file:，字符串类型，可选项，若不设置则存储于系统路径中  
> 
> **width**：拍照后生成图片宽度，高度按等比例压缩，数字，单位px，可选参数，默认不压缩；
> 
> **compress**：图片压缩后质量比，字，取值[1~100]，默认100
> 
> - 1：图片按最高压缩比例进行压缩；
> 
> - 100：图片不压缩
> 
> **isFront**：是否默认启动前置摄像头,bool型
> 
> - true：启用摄像头；
> - false：启用后置摄像头（默认）
> 
> **isCrop**：拍照生成图片是否进行裁剪,bool型，取值[true,false]
> 
> - true：裁剪；
> 
> - false：不裁剪（默认）
> 
> **cropWidth**：裁剪图片宽度，数字，单位px。  
> 
> **isAlbum**：拍照后生成图片是否保存至系统相册，bool型,可选项
> 
> - true：拍照后生成图片保存至系统相册；
> 
> - false：拍照后生成图片不保存至系统相册（默认）

callFunction：回调函数，回调参数为Json对象，定义如下：  

> **code**：拍照/摄像结果，数字[0,-1]
> 
> - 0：拍照/摄像成功；
> 
> - -1：用户取消；
> 
> **path**：生成文件完整全路径，字符串类型；

