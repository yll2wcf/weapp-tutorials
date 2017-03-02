##获取context对象

绘图的第一步：创建一个Canvas绘图的上下文，也就是绘图的场景。小程序给我们提供了多种方法：

###wx.createCanvasContext(canvasId)

创建 canvas 绘图上下文（指定 canvasId）

注意这里需要指定canvasId，该绘图上下文只作用于对应的画布组件 

参数（表8-70）：
表8-70

|参数	|类型	|说明|
| :--- | :--- | :--- |
|canvasId	|String	|画布表示，传入定义在画布的 canvas-id|

示例代码:

```xml
<canvas canvas-id="myCanvas" style="border: 1px solid;"/>
```
（本节所有画布的布局文件都使用这行代码，下文不再重复）
```js
const ctx = wx.createCanvasContext('myCanvas')
```

###wx.createContext (不推荐使用)
创建并返回绘图上下文。
使用方法与createCanvasContext类似，但是由于没有id，可能会导致混乱，所以不建议使用这种方法。

###drawCanvas (不推荐使用)

用所提供的 actions 在所给的 canvas-id 对应的 canvas 上进行绘图。

参数（表8-71）：
表8-71

|参数	|类型	|说明|
| :--- | :--- | :--- |
|canvasId	|String|	画布标识，传入 <canvas/> 的 cavas-id|
|actions	|Array	|绘图动作数组，由 wx.createContext 创建的 context，调用 getActions 方法导出绘图动作数组。|
|reserve	|Boolean	|(可选)本次绘制是否接着上一次绘制，即reserve参数为false，则在本次调用drawCanvas绘制之前native层应先清空画布再继续绘制；若reserver参数为true，则保留当前画布上的内容，本次调用drawCanvas绘制的内容覆盖在上面，默认 false|

实例代码：

```js
wx.drawCanvas({
          canvasId: 'canvas',
          actions: this.context.getActions()
        })
```
与讲解画布组件时的例子一样，使用“this.context.”来创建绘图动作，然后调用drawCanvas绘制。

###canvasToTempFilePath(OBJECT)
把当前画布的内容导出生成图片，并返回文件路径

OBJECT参数说明（表8-72）：
表8-72

|参数	|类型	|必填	|说明|
| :--- | :--- | :--- |:--- |
|canvasId	|String|	是	|画布标识，传入画布的cavas-id|
|success	|Function	|否	|接口调用成功的回调函数|
|fail	|Function	|否	|接口调用失败的回调函数|
|complete	|Function	|否	|接口调用结束的回调函数（调用成功、失败都会执行）|

示例代码：
```js
wx.canvasToTempFilePath({
  canvasId: 'myCanvas',
  success(res) {                       //成功后控制台输出文件保存路径
    console.log(res.tempFilePath)
  } 
})
```