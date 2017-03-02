#4.3 WXSS基本属性

WXSS和CSS一样，样式设置有很多，足够一本书介绍的了。我们不可能在这一节中介绍完。其实好多属性也没必要死记，我们可以在需要的时候查阅文档。
文档地址:http://www.phpstudy.net/css3/

我们就先介绍几个基本的常用的，参考下面代码:

```xml
<!--wxml-->
<view>小程序</view>
```
```css
/*WXSS*/
View{
    width: 200rpx;
    height: 200rpx;
    background-color: blue; 
    color: red;
    font-size: 50rpx;
}
```
上面我们用到了几个属性就是最基本的属性了。

1. `width` 组件的宽度
2. `height` 组件的高度
3. `background-color` 组件的背景颜色，代码中定义的蓝色
4. `color` 内容的颜色，代码中定义的红色。
5. `font-size` 字体的大小

注意: 代码中用到的尺寸单位`rpx` 参考4.4。

代码运行结果，参考图4-8。
![](/assets/图4-8.png) 图4-8 运行结果



