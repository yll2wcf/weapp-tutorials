####矩形

#####rect
创建一个矩形，需要用 fill() 或者 stroke() 方法将矩形真正的画到 canvas 中。

参数（表8-79）：
表8-79

|参数	|类型	|说明|
| :--- | :--- | :--- |
|x	|Number	|矩形路径左上角的x坐标|
|y	|Number	|矩形路径左上角的y坐标|
|width	|Number	|矩形路径的宽度|
|height	|Number|	矩形路径的高度|

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    ctx.rect(10, 10, 150, 75)
    ctx.setFillStyle('red')
    ctx.fill()
    ctx.draw()
  },
})
```
#####fillRect
填充一个矩形。用 setFillStyle() 设置矩形的填充色，如果没设置默认是黑色。

#####strokeRect
画一个矩形(非填充)。用 setFillStroke() 设置矩形线条的颜色，如果没设置默认是黑色。

参数同rect部分，示例请参考“颜色，样式，阴影”部分。

#####clearRect
清除画布上在该矩形区域内的内容。clearRect并非画一个白色的矩形在地址区域，而是清空，就像是用橡皮擦掉画布上的矩形区域，使之变回画布原来的颜色。所以如果我们为画布在wsxx文件或使用style添加了彩色的背景，那么就不是白色而是背景色了。

参数同rect。

示例代码：
```
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    ctx.setFillStyle('red')
    ctx.fillRect(10, 10, 150, 100) 
    ctx.clearRect(10, 10, 50, 75)
    ctx.draw()
  },
})
```