####其他

#####setGlobalAlpha
设置全局画笔透明度。

参数：

|参数	|类型	|范围	|说明|
| :--- | :--- | :--- |:--- |
|alpha	|Number|	0~1|	透明度，0 表示完全透明，1 表示完全不透明|

#####save
保存当前的绘图上下文。

#####restore
恢复之前保存的绘图上下文。

save和restore方法必须是配对使用的，restore方法前必须有save方法。restore方法的调用只影响restore之后绘制的内容，对restore之前已经绘制到屏幕上的图形不会产生任何影响。

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    //先保存了原始的画布状态
    ctx.save()
    ctx.strokeRect(100, 10, 150, 100)
    ctx.rotate(20 * Math.PI / 180)
    ctx.strokeRect(100, 10, 150, 100)
    ctx.rotate(20 * Math.PI / 180)
    //画布旋转了两次，但调用restore后会恢复save时的状态，即原始状态
    ctx.restore()
    ctx.setStrokeStyle('red')
    ctx.strokeRect(100, 10, 150, 100)

    ctx.draw()
  },
})
```

运行结果如图8-7-27：
![](/assets/8-7-27.png)图8-7-27

#####draw
将之前在绘图上下文中的描述（路径、变形、样式）画到canvas中。绘图上下文需要由wx.createCanvasContext(canvasId)来创建。

参数：

|参数	|类型	|说明|
| :--- | :--- | :--- |
|reserve	|Boolean	|非必填。本次绘制是否接着上一次绘制，即reserve参数为false，则在本次调用drawCanvas绘制之前native层应先清空画布再继续绘制；若reserver参数为true，则保留当前画布上的内容，本次调用drawCanvas绘制的内容覆盖在上面，默认false|