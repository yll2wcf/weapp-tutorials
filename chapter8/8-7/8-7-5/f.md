##变形

所有的变形效果指的都是画布的变形效果。

###scale
在调用scale方法后，之后创建的路径其横纵坐标会被缩放。多次调用scale，倍数会相乘。

参数（表8-88）：
表8-88

|参数	|类型	|说明|
| :--- | :--- | :--- |
|scaleWidth	|Number	|横坐标缩放的倍数 (1 = 100%，0.5 = 50%，2 = 200%)|
|scaleHeight	|Number	|纵坐标轴缩放的倍数 (1 = 100%，0.5 = 50%，2 = 200%)|

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')

    ctx.strokeRect(10, 10, 25, 15)
    ctx.scale(2, 2)
    ctx.strokeRect(10, 10, 25, 15)
    ctx.scale(2, 2)
    ctx.strokeRect(10, 10, 25, 15)

    ctx.draw()
  },
})
```
结果如图8-28：
![](/assets/8-28.png)图8-28

###rotate
以原点（默认为（0，0））为中心，原点可以用 translate方法修改。顺时针旋转当前坐标轴。多次调用rotate，旋转的角度会叠加。

参数（表8-89）：
表8-89

|参数	|类型	|说明|
| :--- | :--- | :--- |
|rotate	|Number	|旋转角度，以弧度计(degrees * Math.PI/180；degrees范围为0~360)|

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')

    ctx.strokeRect(100, 10, 150, 100)
    ctx.rotate(20 * Math.PI / 180)
    ctx.strokeRect(100, 10, 150, 100)
    ctx.rotate(20 * Math.PI / 180)
    ctx.strokeRect(100, 10, 150, 100)

    ctx.draw()
  },
})
```
运行结果如图8-29：

![](/assets/8-29.png)图8-29

###translate
对当前坐标系的原点(0, 0)进行变换，默认的坐标系原点为页面左上角。

参数（表8-90）：
表8-90

|参数	|类型	|说明|
| :--- | :--- | :--- |
|x	|Number	|水平坐标平移量|
|y	|Number|	竖直坐标平移量|

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')

    ctx.strokeRect(10, 10, 150, 100)
    ctx.translate(20, 20)
    ctx.strokeRect(10, 10, 150, 100)
    ctx.translate(20, 20)
    ctx.strokeRect(10, 10, 150, 100)

    ctx.draw()
  },
})
```

运行结果如图8-30：
![](/assets/8-30.png)图8-30