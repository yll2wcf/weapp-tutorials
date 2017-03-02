##颜色，样式，阴影

###setFillStyle

设置填充色。如果没有设置 fillStyle，默认颜色为 black。

参数（表8-73）：
表8-73

|参数	|类型	|说明|
| :--- | :--- | :--- |
|color	|Color 	|填充色|

示例代码：
```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    ctx.setFillStyle('red')
    ctx.fillRect(10, 10, 150, 75)                //表示绘制矩形
    ctx.draw()
  },
})
```
运行结果（图8-17）：
![](/assets/8-17.png)图8-17 填充API示例图

###setStrokeStyle

设置边框颜色。如果没有设置 fillStyle，默认颜色为 black。

参数（表8-74）：
表8-74

|参数	|类型	|说明|
| :--- | :--- | :--- |
|color	|Color 	|边框色|

示例代码：
```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    ctx.setFillStyle('red')
    ctx.fillRect(10, 10, 150, 75)                //表示绘制矩形
    ctx.setStrokeStyle('black')
    ctx.strokeRect(10, 10, 150, 75)               //表示绘制边框
    ctx.draw()
  },
})
```
运行结果（图8-18）：
![](/assets/8-18.png)图8-18 边框颜色API示例图

###setShadow
设置阴影样式。如果没有设置，offsetX 默认值为0， offsetY 默认值为0， blur 默认值为0，color 默认值为 black。

参数（表8-75）：
表8-75

|参数	|类型	|范围	|定义|
| :--- | :--- | :--- |:--- |
|offsetX	|Number	|	|阴影相对于形状在水平方向的偏移|
|offsetY	|Number	|	|阴影相对于形状在竖直方向的偏移|
|blur	|Number	|0~100|	阴影的模糊级别，数值越大越模糊|
|color	|Color	|	|阴影的颜色|

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    ctx.setFillStyle('red')
    ctx.setShadow(10, 50, 50, 'blue')           //注意这行代码的位置
    ctx.fillRect(10, 10, 150, 75)               //表示绘制矩形
    ctx.setStrokeStyle('black')
    ctx.strokeRect(10, 10, 150, 75)             //表示绘制边框
    ctx.draw()
  },
```
运行结果（图8-19）：
![](/assets/8-19.png) 图8-19 阴影API示例图
这里要注意setShadow的位置，在fillRect前则阴影为整个矩形阴影，在fillRect之后strokeRect之前则只有边框阴影，如果在strokeRect之后则没有阴影效果。也就是说，阴影的设置要在绘制想要添加阴影的图形之前。
