##线条样式

###setLineWidth

设置线条的宽度。

参数（表8-80）:
表8-80

|参数	|类型	|说明|
| :--- | :--- | :--- |
|lineWidth	|Number	|线条的宽度(单位是px)|

###setLineCap
设置线条的端点样式。

参数（表8-81）:
表8-81

| 参数	| 类型	| 范围	| 说明| 
| :--- | :--- | :--- |:--- |
| lineCap	| String	| 'butt'、'round'、'square'	| 线条的结束端点样式| 

* butt: 默认。向线条的每个末端添加平直的边缘。
* round: 向线条的每个末端添加圆形线帽。
* square: 向线条的每个末端添加正方形线帽。

###setLineJoin

设置线条的交点样式。

参数（表8-82）:
表8-82

| 参数	| 类型	| 范围	| 说明| 
| :--- | :--- | :--- |:--- |
|lineJoin	|String	|'bevel'、'round'、'miter'|	线条的结束交点样式|

* bevel: 创建斜角。
* round: 创建圆角。
* miter: 默认。创建尖角。

示例代码：
```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    //默认属性，有关绘制路线的方法会在下一节介绍
    ctx.beginPath()
    ctx.moveTo(10, 10)
    ctx.lineTo(100, 50)
    ctx.lineTo(10, 90)
    ctx.stroke()
    //10线宽，平直线端，斜角交点
    ctx.beginPath()
    ctx.setLineJoin('bevel')
    ctx.setLineCap('butt')
    ctx.setLineWidth(10)
    ctx.moveTo(50, 10)
    ctx.lineTo(140, 50)
    ctx.lineTo(50, 90)
    ctx.stroke()
    //10线宽，圆形线端，圆角交点
    ctx.beginPath()
    ctx.setLineJoin('round')
    ctx.setLineCap('round')
    ctx.setLineWidth(10)
    ctx.moveTo(90, 10)
    ctx.lineTo(180, 50)
    ctx.lineTo(90, 90)
    ctx.stroke()
    //10线宽，方形线端，尖角交点
    ctx.beginPath()
    ctx.setLineJoin('miter')
    ctx.setLineCap('square')
    ctx.setLineWidth(10)
    ctx.moveTo(130, 10)
    ctx.lineTo(220, 50)
    ctx.lineTo(130, 90)
    ctx.stroke()

    ctx.draw()
  },
})
```

运行结果（图8-22）：

![](/assets/8-22.png)图8-22

###setMiterLimit

设置最大斜接长度，斜接长度指的是在两条线交汇处内角和外角之间的距离。 当 setLineJoin() 为 miter 时才有效。超过最大倾斜长度的，连接处将以 lineJoin 为 bevel 来显示。

参数（表8-83）：
表8-83

|参数	|类型	|说明|
| :--- | :--- | :--- |
|miterLimit	|Number	|最大斜接长度|

示例代码：

```js
...
ctx.beginPath()
ctx.setLineWidth(10)
ctx.setLineJoin('miter')
ctx.setMiterLimit(2)
ctx.moveTo(50, 10)
ctx.lineTo(140, 50)
ctx.lineTo(50, 90)
ctx.stroke()
...

```
倾斜长度如下图（图8-23）所示，边角的角度越小，斜接长度就会越大。为了避免斜接长度过长，我们可以使用miterLimit属性。如果斜接长度超过miterLimit的值，边角会以lineJoin的"bevel"类型来显示（图解 3）

![](/assets/8-23.png)图8-23