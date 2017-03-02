#### 文字与图片

##### setFontSize
设置字体的字号。数字越大，字体越大。

参数（表8-91）：
表8-91

|参数	|类型	|说明|
| :--- | :--- | :--- |
|fontSize   | Number   | 字体的字号|

#####fillText
在画布指定位置绘制被填充的文本。

参数（表8-92）：
表8-92

|参数	|类型	|说明|
| :--- | :--- | :--- |
|text	|String	|在画布上输出的文本|
|x	|Number	|绘制文本的左上角x坐标位置|
|y	|Number	|绘制文本的左上角y坐标位置|

#####drawImage
绘制图像，图像源可以是本地图片或网络图片。

参数（表8-93）：
表8-93

|参数	|类型	|说明|
| :--- | :--- | :--- |
|imageResource|	String	|所要绘制的图片资源|
|x	|Number|	图像左上角的x坐标|
|y	|Number	|图像左上角的y坐标|
|width	|Number	|图像宽度|
|height	|Number|	图像高度|

示例代码：

```js
Page({
  onLoad: function () {
    const ctx = wx.createCanvasContext('myCanvas')
    ctx.drawImage("../../utils/image.png", 0, 0, 150, 100)
    ctx.draw()
  },
})
```

运行结果如图8-31：
![](/assets/8-31.png)图8-31

这里使用的图片为保存在utils文件夹下的一张图片，加载网络图片的话直接使用url地址即可。图片会根据设置的宽高拉伸。