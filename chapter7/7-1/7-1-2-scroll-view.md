# 7-1-2 scroll-view

scroll-view组件，它用来定义一个可滚动的视图区域，相当于ios开发中的UIScrollView。里面的内容如果超过这个区域的宽或高时，就会出现滚动条。  
scroll-view包含的属性：

| 属性名 | 类型 | 默认值 | 注释 |
| :--- | :--- | :--- | :--- |
| scroll-x | Boolean | false | 允许横向滚动 |
| scroll-y | Boolean | false | 允许纵向滚动 |
| upper-threshold | Number | 50 | 距顶部/左边多远时（单位px），触发 scrolltoupper 事件 |
| lower-threshold | Number | 50 | 距底部/右边多远时（单位px），触发 scrolltolower 事件 |
| scroll-top | Number |  | 设置竖向滚动条位置 |
| scroll-left | Number |  | 设置横向滚动条位置 |
| scroll-into-view | String |  | 值应为某子元素id，则滚动到该元素，元素顶部对齐滚动区域顶部 |
| bindscrolltoupper | EventHandle |  | 滚动到顶部/左边，会触发 scrolltoupper 事件 |
| bindscrolltolower | EventHandle |  | 滚动到底部/右边，会触发 scrolltolower 事件 |
| bindscroll | EventHandle |  | 滚动时触发，event.detail = {scrollLeft, scrollTop, scrollHeight, scrollWidth, deltaX, deltaY} |

示例代码：  
wxml中：

```
<view class="viewTitle">
    <text class="titleName">ScrollView视图展示</text>
  </view>
  <!--样式一，竖向滑动-->
<view class="section">
    <view class="section__title">样式一，竖向滑动Vertical</view>
    <view class="flex-wrp">
    <!--bindscrolltoupper后面的参数可以不写，在.js文件中
    有对应的交互方法-->
      <scroll-view scroll-y="true" style="height: 200px;" 
      bindscrolltoupper="upper" bindscrolltolower="lower" 
      bindscroll="scroll" scroll-into-view="{{toView}}" 
      scroll-top="{{scrollTop}}">
        <view id="blue" class="scroll-view-item bc_blue"></view>
        <view id="yellow"  class="scroll-view-item bc_yellow"></view>
        <view id="red" class="scroll-view-item bc_red"></view>
        <view id="green" class="scroll-view-item bc_green"></view>
      </scroll-view>
    </view>
</view>
<!--样式二，横向滑动-->
<view class="section">
    <view class="section__title">样式二，横向滑动Horizontal</view>
    <view class="flex-wrp">
    <scroll-view class="scroll-view_H" scroll-x="true" bindscroll="scroll" style="width: 100%">
        <view id="green" class="scroll-view-item_H bc_green"></view>
        <view id="red"  class="scroll-view-item_H bc_red"></view>
        <view id="yellow" class="scroll-view-item_H bc_yellow"></view>
        <view id="blue" class="scroll-view-item_H bc_blue"></view>
      </scroll-view>
    </view>
</view>
```

wxss中：

```
.flex-wrp {
    height:400rpx;
    display:flex;
    background-color:#ffffff;
}
.scroll-view-item {
    width:800rpx;
    height:200rpx;
}
.scroll-view_H {
    white-space:nowrap;
}
.scroll-view-item_H {
    display:inline-block;
    width:100%;
    height:400rpx;
}
.bc_green {
    background-color:#09BB07;
}
.bc_red {
    background-color:#F76260;
}
.bc_blue {
    background-color:#10AEFF;
}
.bc_yellow {
    background-color:#FFBE00;
}
```

运行效果如图7-2所示：

![](/assets/图7-2 scroll-view组件演示.png)

注意:
- 请勿在 scroll-view 中使用 textarea、map、canvas、video 组件
- scroll-into-view 的优先级高于 scroll-top
- 在滚动 scroll-view 时会阻止页面回弹，所以在 scroll-view 中滚动，是无法触发 onPullDownRefresht
- 若要使用下拉刷新，请使用页面的滚动，而不是 scroll-view ，这样也能通过点击顶部状态栏回到页面顶部

