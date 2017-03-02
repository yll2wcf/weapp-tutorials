#7.7.1 canvas
canvas 画布组件，可用于画出任意形状，实现页面动画，canvas 标签默认宽度300px、高度225px。并且同一页面中的 canvas-id 不可重复，如果使用一个已经出现过的 canvas-id，该 canvas 标签对应的画布将被隐藏并不再正常工作
canvas 所包含的属性，如表7-37所示：

表7-37

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| canvas-id | String |  | canvas 组件的唯一标识符 |
| disable-scroll | Boolean | false | 当在 canvas 中移动时，禁止屏幕滚动以及下拉刷新 |
| bindtouchstart | EventHandle |  | 手指触摸动作开始 |
| bindtouchmove | EventHandle |  | 手指触摸后移动 |
| bindtouchend | EventHandle |  | 手指触摸动作结束 |
| bindtouchcancel | EventHandle |  | 手指触摸动作被打断，如来电提醒，弹窗 |
| bindlongtap | EventHandle |  | 手指长按 500ms 之后触发，触发了长按事件后进行移动不会触发屏幕的滚动 |
| binderror | EventHandle |  | 当发生错误时触发 error 事件，detail = {errMsg: 'something wrong'} |

示例代码：
wxml中：
```xml
<view class="container">
  <view class="canvas_area">
    <!--注意：同一页面中的 canvas-id 不可重复，如果使用一个已经出现过的 canvas-id，该 canvas 标签对应的画布将被隐藏并不再正常工作-->
    <canvas canvas-id="myCanvas" class="myCanvas" disable-scroll="false" bindtouchstart="touchStart" bindtouchmove="touchMove" bindtouchend="touchEnd">
    </canvas>
  </view>
  <view class="canvas_tools">
    <view class="box box1" bindtap="penSelect" data-param="5">细体</view>
    <view class="box box2" bindtap="penSelect" data-param="15">粗体</view>
    <view class="box box3" bindtap="colorSelect" data-param="#FF3300"></view>
    <view class="box box4" bindtap="colorSelect" data-param="#FFFF00"></view>
    <view class="box box5" bindtap="clearCanvas">清除</view>
  </view>
</view>
```
js中：
```js
Page({
  data: {
    pen: 3, //画笔粗细默认值
    color: '#33CC00' //画笔颜色默认值
  },
  startX: 0, //保存X坐标轴变量
  startY: 0, //保存X坐标轴变量
  isClear: false, //是否启用橡皮擦标记
  //手指触摸动作开始
  touchStart: function (e) {
    //得到触摸点的坐标
    this.startX = e.changedTouches[0].x
    this.startY = e.changedTouches[0].y
    this.context = wx.createContext()

    if (this.isClear) { //判断是否启用的橡皮擦功能  ture表示清除  false表示画画
      this.context.setStrokeStyle('#F8F8F8') //设置线条样式 此处设置为画布的背景颜色  清除按钮原理就是：利用擦过的地方被填充为画布的背景颜色一致 从而达到清除的效果 
      this.context.setLineCap('round') //设置线条端点的样式
      this.context.setLineJoin('round') //设置两线相交处的样式
      this.context.setLineWidth(20) //设置线条宽度
      this.context.save();  //保存当前坐标轴的缩放、旋转、平移信息
      this.context.beginPath() //开始一个路径 
      this.context.arc(this.startX, this.startY, 5, 0, 2 * Math.PI, true);  //添加一个弧形路径到当前路径，顺时针绘制  这里总共画了360度  也就是一个圆形 
      this.context.fill();  //对当前路径进行填充
      this.context.restore();  //恢复之前保存过的坐标轴的缩放、旋转、平移信息
    } else {
      this.context.setStrokeStyle(this.data.color)
      this.context.setLineWidth(this.data.pen)
      this.context.setLineCap('round') // 让线条圆润 
      this.context.beginPath()
    }
  },
  //手指触摸后移动
  touchMove: function (e) {
    var startX1 = e.changedTouches[0].x
    var startY1 = e.changedTouches[0].y
    if (this.isClear) { //判断是否启用的橡皮擦功能  ture表示清除  false表示画画
      this.context.save();  //保存当前坐标轴的缩放、旋转、平移信息
      this.context.moveTo(this.startX, this.startY);  //把路径移动到画布中的指定点，但不创建线条
      this.context.lineTo(startX1, startY1);  //添加一个新点，然后在画布中创建从该点到最后指定点的线条
      this.context.stroke();  //对当前路径进行描边
      this.context.restore()  //恢复之前保存过的坐标轴的缩放、旋转、平移信息
      this.startX = startX1;
      this.startY = startY1;
    } else {
      this.context.moveTo(this.startX, this.startY)
      this.context.lineTo(startX1, startY1)
      this.context.stroke()
      this.startX = startX1;
      this.startY = startY1;
    }
    //只是一个记录方法调用的容器，用于生成记录绘制行为的actions数组。context跟<canvas/>不存在对应关系，一个context生成画布的绘制动作数组可以应用于多个<canvas/>
    wx.drawCanvas({
      canvasId: 'myCanvas',
      reserve: true,
      actions: this.context.getActions() // 获取绘图动作数组
    })
  },
  //手指触摸动作结束
  touchEnd: function () {

  },
  //启动清除按钮方法
  clearCanvas: function () {
    if (this.isClear) {
      this.isClear = false;
    } else {
      this.isClear = true;
    }
  },
  //更改画笔大小的方法
  penSelect: function (e) { 
    console.log(e.currentTarget);
    this.setData({ pen: parseInt(e.currentTarget.dataset.param) });
    this.isClear = false;
  },
  //更改画笔颜色的方法
  colorSelect: function (e) { 
    console.log(e.currentTarget);
    this.setData({ color: e.currentTarget.dataset.param });
    this.isClear = false;
  }
})
```
**注意:**

* `canvas`组件是由客户端创建的原生组件，它的层级是最高的。
* 请勿在`scroll-view`中使用`canvas`组件。
* css 动画对`canvas`组件无效。



