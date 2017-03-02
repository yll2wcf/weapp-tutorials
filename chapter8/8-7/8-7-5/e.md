##路径

###fill

对当前路径中的内容进行填充。默认的填充色为黑色。如果当前路径没有闭合，fill()方法会将起点和终点进行连接，然后填充。fill()填充的的路径是从beginPath()开始计算，但是不会将fillRect()包含进去。

###stroke

画出当前路径的边框。默认颜色色为黑色。stroke()描绘的的路径是从beginPath()开始计算，但是不会将strokeRect()包含进去。

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    //绘制一个矩形边框
    ctx.rect(10, 10, 100, 30)
    ctx.setStrokeStyle('yellow')
    ctx.stroke()
    //开始绘制路径
    ctx.beginPath()
    ctx.rect(10, 40, 100, 30)
    //yellow的设置只作用于下一个strokeRect
    ctx.setStrokeStyle('yellow')
    ctx.strokeRect(10, 70, 100, 30)
    ctx.rect(10, 100, 100, 30)
    //为当前路径添加边框
    ctx.setStrokeStyle('red')
    ctx.stroke()
    //平移后绘制不闭合的两个直线
    ctx.moveTo(300, 10)
    ctx.lineTo(200, 10)
    ctx.lineTo(200, 100)
    //填充当前路径
    ctx.fill()
    ctx.draw()
  },
})
```
运行结果（图8-24）：
![](/assets/8-24.png)图8-24

fill与stroke的目标都是从调用beginPath()才开始，使用strokeRect（fillRect）的部分不包含在这之内，另外不闭合的区域在使用fill时会先自动闭合（连接起点终点）。

###beginPath

开始创建一个路径，需要调用fill或者stroke才会使用路径进行填充或描边，也就是说每绘制一次路径，我们需要先调用beginPath()（除第一次以外，在建立canvas布局时系统会帮我们准备好，相当于调用了一次 beginPath()），然后调用绘制路径的API，最后通过调用fill()或stroke()方法来使我们的路径绘制在画布上。同一个路径内的多次setFillStyle()、setStrokeStyle()、setLineWidth()等设置，以最后一次设置为准。

###closePath

关闭一个路径，关闭路径会连接起点和终点。如果关闭路径后没有调用 fill() 或者 stroke() 并开启了新的路径，那之前的路径将不会被渲染。

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    //第一条路径，关闭前未调用fill()/stroke()
    ctx.rect(10, 10, 100, 30)
    ctx.closePath()

    //第二条路径
    ctx.beginPath()
    ctx.rect(10, 40, 100, 30)

    //使用fillRect填充蓝色区域
    ctx.setFillStyle('blue')
    ctx.fillRect(10, 70, 100, 30)
    
    //绘制矩形，设置填充色为黄色
    ctx.setFillStyle('yellow')
    ctx.rect(10, 100, 100, 30)

    //填充当前路径，红色
    ctx.setFillStyle('red')
    ctx.fill()
    ctx.draw()
  },
})
```
运行结果如图8-25：
![](/assets/8-25.png)图8-25

第一个矩形因为没有调用fill/stroke，所以没有渲染，蓝色区域相当于第二天路径外，设置红色不会影响这一部分。而黄色的设置被更后边的红色设置覆盖了，所以第四个矩形仍然为红色。

###moveTo

把路径移动到画布中的指定点，不创建线条。

###lineTo

增加一个新点，然后创建一条从上次指定点到目标点的线。用 stroke() 方法来画线条。

moveTo与lineTo的参数（表8-84）：
表8-84

|参数	|类型	|说明|
| :--- | :--- | :--- |
|x	|Number	|目标位置的x坐标|
|y	|Number	|目标位置的y坐标|

###arc
画一条弧线。创建一个圆可以用arc()方法指定其起始弧度为0，终止弧度为2 * Math.PI。用stroke()或者fill()方法来在canvas中画弧线。

参数（表8-85）：
表8-85

|参数	|类型	|说明|
| :--- | :--- | :--- |
|x	|Number	|圆的x坐标|
|y	|Number|	圆的y坐标|
|r	|Number|	圆的半径|
|sAngle	|Number	|起始弧度，单位弧度（在3点钟方向）|
|eAngle	|Number	|终止弧度|
|counterclockwise	|Boolean	|可选。指定弧度的方向是逆时针还是顺时针。默认是false，即顺时针。|

示例代码：
```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    //绘制圆形背景，颜色为“#EEEEEE”
    ctx.arc(100, 75, 50, 0, 2 * Math.PI)
    ctx.setFillStyle('#EEEEEE')
    ctx.fill()
    //绘制横轴（40，75）到（160，75）与纵轴（100，15）到（100，135），颜色为“#AAAAAA”
    ctx.beginPath()
    ctx.moveTo(40, 75)
    ctx.lineTo(160, 75)
    ctx.moveTo(100, 15)
    ctx.lineTo(100, 135)
    ctx.setStrokeStyle('#AAAAAA')
    ctx.stroke()
    //绘制文字
    ctx.setFontSize(12)
    ctx.setFillStyle('black')
    ctx.fillText('0', 165, 78)
    ctx.fillText('0.5*PI', 83, 145)
    ctx.fillText('1*PI', 15, 78)
    ctx.fillText('1.5*PI', 83, 10)
    //绘制三个点，其实就是绘制半径很小的圆，每次需要先调用beginPath()
    //圆心
    ctx.beginPath()
    ctx.arc(100, 75, 2, 0, 2 * Math.PI)
    ctx.setFillStyle('lightgreen')
    ctx.fill()
    //起始弧度
    ctx.beginPath()
    ctx.arc(100, 25, 2, 0, 2 * Math.PI)
    ctx.setFillStyle('blue')
    ctx.fill()
    //终止弧度
    ctx.beginPath()
    ctx.arc(150, 75, 2, 0, 2 * Math.PI)
    ctx.setFillStyle('red')
    ctx.fill()
    //绘制3/4圆的弧线
    ctx.beginPath()
    ctx.arc(100, 75, 50, 0, 1.5 * Math.PI)
    ctx.setStrokeStyle('#333333')
    ctx.stroke()

    ctx.draw()
  },
})
```
运行结果如图8-26所示：
![](/assets/8-26.png)图8-26

###quadraticCurveTo

创建二次贝塞尔曲线路径。贝塞尔曲线是在计算机绘图中生产任意曲线的重要工具，通过起点（在这里曲线的起始点为路径中前一个点），终点与控制点（可能有多个，二次贝塞尔曲线的控制点为1个，控制点越多次数越高）来确定。

参数（表8-86）：
表8-86

|参数	|类型	|说明|
| :--- | :--- | :--- |
|cpx	|Number|	贝塞尔控制点的x坐标|
|cpy	|Number	|贝塞尔控制点的y坐标|
|x	|Number	|结束点的x坐标|
|y	|Number	|结束点的y坐标|

###bezierCurveTo

创建三次方贝塞尔曲线路径。与二次贝塞尔曲线类似，控制点由1个变为2个。

参数（表8-87）：
表8-87

|参数	|类型	|说明|
| :--- | :--- | :--- |
|cp1x	|Number	|第一个贝塞尔控制点的 x 坐标|
|cp1y	|Number	|第一个贝塞尔控制点的 y 坐标|
|cp2x	|Number	|第二个贝塞尔控制点的 x 坐标|
|cp2y	|Number	|第二个贝塞尔控制点的 y 坐标|
|x	|Number	|结束点的 x 坐标|
|y	|Number	|结束点的 y 坐标|

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    //二次贝塞尔曲线，颜色为红色
    ctx.beginPath()
    ctx.moveTo(20, 20)
    ctx.quadraticCurveTo(20, 100, 200, 20)
    ctx.setStrokeStyle('red')
    ctx.stroke()
    //三次贝塞尔曲线，颜色为绿色
    ctx.beginPath()
    ctx.moveTo(20, 20)
    ctx.bezierCurveTo(20, 100, 200, 100, 200, 20)
    ctx.setStrokeStyle('green')
    ctx.stroke()

    ctx.draw()
  },
})
```

运行结果如图8-27：
![](/assets/8-27.png)图8-27
