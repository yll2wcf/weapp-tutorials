####路径

#####fill

对当前路径中的内容进行填充。默认的填充色为黑色。如果当前路径没有闭合，fill()方法会将起点和终点进行连接，然后填充。fill()填充的的路径是从beginPath()开始计算，但是不会将fillRect()包含进去。

#####stroke

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
运行结果（图8-7-19）：
![](/assets/8-7-19.png)图8-7-19

fill与stroke的目标都是从调用beginPath()才开始，使用strokeRect（fillRect）的部分不包含在这之内，另外不闭合的区域在使用fill时会先自动闭合（连接起点终点）。


