##4.5 css和wxss的区别

WXSS具有CSS大部分特性，同时为了满足小程序开发的要求（主要体现在不同手机屏幕的适配问题），WXSS对CSS进行了扩充修改，与CSS相比，WXSS的特性有：

* 尺寸单位
* 样式导入

###尺寸单位

WXSS新增的两种尺寸单位为：rpx与rem，和原有尺寸相比，这两种尺寸单位会根据手机屏幕尺寸而改变，从而更好地适配不同尺寸的屏幕。

rpx（responsive pixel）: 可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx。如在iPhone6上，屏幕宽度为375px，共有750个物理像素，则750rpx = 375px = 750物理像素，1rpx = 0.5px = 1物理像素。在不同尺寸手机上rpx和px转换算法如表4-4所示

表4-4

|设备	|rpx换算px (屏幕宽度/750)	|px换算rpx (750/屏幕宽度)|
|:--|:--|:--|
|iPhone5	|1rpx = 0.42px	|1px = 2.34rpx|
|iPhone6/7	|1rpx = 0.5px	|1px = 2rpx|
|iPhone6/7 plus	|1rpx = 0.552px	|1px = 1.81rpx|
rem（root em）: 规定屏幕宽度为20rem；1rem = (750/20)rpx 。

建议在开发微信小程序时设计师可以用iPhone6作为视觉稿的标准，模拟器默认的设备也是iphone6。

在较小的屏幕上不可避免的会有一些毛刺，请在开发时尽量避免这种情况。

###样式导入

使用@import语句可以导入外联样式表，@import后跟需要导入的外联样式表的相对路径，用;表示语句结束。
示例代码：
```css
/** common.wxss **/
.small-p{
  padding:5px;
}

/** app.wxss **/
@import "common.wxss";
.middle-p:{
  padding:15px;
}
```
###内联样式

小程序组件除了支持`class`，`id`等还支持使用`style`属性来控制组件的样式。

`style`控制的样式优先级最高，和css不一样的是，`style`属性的值支持`{{...}}`动态设置。

一般静态的样式统一写到class中。style接收动态的样式，在运行时会进行解析，所以不要将静态的样式写进style中，以免影响渲染速度。
```xml
   <view style="color:{{color}};" />
```


###全局样式与局部样式

定义在app.wxss中的样式为全局样式，作用于每一个页面。在page的wxss文件中定义的样式为局部样式，只作用在对应的页面，并会覆盖app.wxss中相同的选择器。
