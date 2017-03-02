###6-4 position属性

除了通过以上方式让系统自动安排布局以外，有些时候我们需要手动设置位置（例如布局属于无规律布局），这时候我们就需要使用position属性。

position可能的值有：

* absolute 表示当前元素相对于第一个非static属性的父组件绝对定位，使用top，bottom，left，right四个键值来决定其到父组件的最上，最下，最左，最右的距离。
* fixed 表示当前元素相对于屏幕绝对定位，同样使用top, bottom, left, right来设定位置。
* relative 表示当前元素相对于上一个同级组件相对定位，使用top，left来设定到上一个同级组件最上沿，最左沿的距离，默认值为0.
* static 默认值，没有定位，会忽略top，bottom，left，right或z-index的声明。
* inherit 表示当前元素继承其父元素的position属性。

这里比较常用的为absolute与relative。

我们来看一个例子，首先在屏幕中间放置一个红色的view，文字居中显示（如图6-10所示）。

![](/assets/6-10.png)图6-10 position属性例图-初始布局

这时的wxss设定为：

```css
.center-view{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%
}

.red{
  display:flex;
  height: 800rpx;
  background-color: red;
  width: 600rpx;
  justify-content: center;
  align-items: center;
  color: #ffffff;
  font-size: 40rpx;
}
```
然后我们想在红色的view里添加一个绿的view，距离红色的顶端与左端各100rpx，按照我们讲的，这种情况适合使用position属性，首先来看relative是否适用，我们将绿色的view添加到红色view里：

```xml
<view class="center-view">
  <view class="red">red
    <view class="green"/>
  </view>
</view> 
```
然后设定绿色view的属性为：

```css
.green{
  height: 200rpx;
  background-color: green;
  width: 200rpx;
  position: relative;
  top: 100rpx;
  left: 100rpx;
}
```
我们来看下这样的结果是什么（如图6-11所示）：
![](/assets/6-11.png)图6-11 position属性例图-relative效果


可以看到绿色方块加入到了红色布局里但是位置不对，这是因为我们在红色view里设定了居中显示，所以根据relative的定义，这里的100rpx距离其实是文字的，而不是其父容器的。

接着我们把relative改成absolute试试看，结果是这样的（图6-12所示）：

![](/assets/6-12.png)图6-12 position属性例图-父布局缺失position属性情况


我们发现绿色方块被移动到了红色view的上方，超出了红色view的范围。这是因为，根据absolute的定义，其相对的是第一个非static的父组件，而红色的view因为没有设定position属性，所以使用默认值static，在系统渲染布局时，对于absolute属性不会根据红色view而是一直向上寻找不为static的父组件，最后设定为了相对于整个布局的位置。为了达到我们要的效果，这里我们为红色的view添加position：relative的属性。

```css
.red{
  display:flex;
  height: 800rpx;
  background-color: red;
  width: 600rpx;
  justify-content: center;
  align-items: center;
  color: #ffffff;
  font-size: 40rpx;
  position: relative;
}

.green{
  height: 200rpx;
  background-color: green;
  width: 200rpx;
  position: absolute;
  top: 100rpx;
  left: 100rpx;
}
```

这样就得到了我们所要的布局样式（图6-13）：

![](/assets/6-13.png)图6-13 position属性例图-正确结果


在设定组件的宽高时，可用的属性有：width，height，maxHeight，maxWidth，minHeight，minWidth。为了发挥flexbox动态改变组件宽高的特性，要尽量不指定组件的宽高，由系统根据组件的内容与设定的排列方式来动态的设定宽高。如果对宽高有要求，尽量设定其最大与最小值，以便其在一定范围内弹性改变（这也有利于配适不同尺寸的手机）。另外，如果必须要设定宽高，那么尽可能只设定其中一项，把另一项交给系统来设定。