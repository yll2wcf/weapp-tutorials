# 7.1.1 view

小程序所有的组件都是建立在view基础上的，view类似于HTML中的`<div>`元素。  
View 包含了一些属性，如表7-4所示：

表7-4

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| hover | Boolean | false | 是否启用点击态 |
| hover-class | String | none | 指定按下去的样式类。当`hover-class="none"`时，没有点击态效果 |
| hover-start-time | Number | 50 | 按住后多久出现点击态，单位毫秒 |
| hover-stay-time | Number | 400 | 手指松开后点击态保留时间，单位毫秒 |

示例代码：  
wxml中：

```xml
<view class="viewTitle">
  <text>View展示</text>
</view>

<!--样式一，横向排列-->
<view class="section">
  <view class="section__title">样式一，横向排列</view>
  <view class="flex-wrp">
    <view class="flex-item bc_green">111</view>
    <view class="flex-item bc_red">222</view>
    <view class="flex-item bc_blue">333</view>
  </view>
</view>

<!--样式二，竖向排列,注意在 .wxml的文件中也可以通过style参数进行样式设计-->
<view class="section">
  <view class="section__title">样式二，竖向排列</view>
  <view class="flex-wrp" style="height:300px">
    <view class="flex-item bc_green" style="margin-top: 0px">111</view>
    <view class="flex-item bc_red" style="margin-top: 100px">222</view>
    <view class="flex-item bc_blue" style="margin-top: 200px">333</view>
  </view>
</view>
```

wxss中，wxss可以直接写css代码设置一些样式。

```css
.flex-wrp {
    height:200rpx;
    display:flex;
    background-color:#ffffff;
}
.flex-item {
    width:200rpx;
    height:200rpx;
    color:#ffffff;
    display:flex;
    justify-content:center;
    align-items:center;
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
```

运行效果如图7-1所示：

![](/assets/图7-1 view组件演示.png)

图7-1 view组件示例运行效果图