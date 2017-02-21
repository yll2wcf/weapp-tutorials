### position属性

除了通过以上方式让系统自动安排布局以外，有些时候我们需要手动设置位置（例如布局属于无规律布局），这时候我们就需要使用position属性。

position可能的值有：

* absolute 表示当前元素相对于第一个非static属性的父组件绝对定位，使用top，bottom，left，right四个键值来决定其到父组件的最上，最下，最左，最右的距离。
* fixed 表示当前元素相对于屏幕绝对定位，同样使用top, bottom, left, right来设定位置。
* relative 表示当前元素相对于上一个同级组件相对定位，使用top，left来设定到上一个同级组件最上沿，最左沿的距离，默认值为0.
* static 默认值，没有定位，会忽略top，bottom，left，right或z-index的声明。
* inherit 表示当前元素继承其父元素的position属性。

这里比较常用的为absolute与relative。

在设定组件的宽高时，可用的属性有：width，height，maxHeight，maxWidth，minHeight，minWidth。为了发挥flexbox动态改变组件宽高的特性，要尽量不指定组件的宽高，由系统根据组件的内容与设定的排列方式来动态的设定宽高。如果对宽高有要求，尽量设定其最大与最小值，以便其在一定范围内弹性改变（这也有利于配适不同尺寸的手机）。另外，如果必须要设定宽高，那么尽可能只设定其中一项，把另一项交给系统来设定。