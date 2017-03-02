# 7-3-1 button

button 按钮，它可以供用户点击，从而触发一些列操作。他有许多属性来控制按钮样式。  
button 包含的属性，如表7-9所示：

表7-9

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| size | String | default | 有效值 default, mini |
| type | String | default | 按钮的样式类型，有效值 primary, default, warn |
| plain | Boolean | false | 按钮是否镂空，背景色透明 |
| disabled | Boolean | false | 是否禁用 |
| loading | Boolean | false | 名称前是否带 loading 图标 |
| form-type | String |  | 有效值：submit, reset，用于 `<form/>` 组件，点击分别会触发 submit/reset 事件 |
| hover-class | String | button-hover | 指定按钮按下去的样式类。当 hover-class="none" 时，没有点击态效果 |
| hover-start-time | Number | 50 | 按住后多久出现点击态，单位毫秒 |
| hover-stay-time | Number | 400 | 手指松开后点击态保留时间，单位毫秒 |

示例代码：

wxml中：

```xml
<view class="content">
  <view class="button_box">
    <button size="default">Content</button>
  </view>
  <view class="button_box">
    <button size="mini">Content</button>
  </view>
  <view class="button_box">
    <button type="default">Content</button>
  </view>
  <view class="button_box">
    <button type="primary">Content</button>
  </view>
  <view class="button_box">
    <button type="warn">Content</button>
  </view>
  <view class="button_box">
    <button type="primary" plain="true">Content</button>
  </view>
  <view class="button_box">
    <button type="primary" disabled="true">Content</button>
  </view>
  <view class="button_box">
    <button type="primary" loading="true">Content</button>
  </view>
  <view class="button_box">
    <button type="primary" fromTyoe="reset">Content</button>
  </view>
  <view class="button_box">
    <button type="primary" hover-class="none">Content</button>
  </view>
</view>
```

运行效果如图7-7所示：

![](/assets/图7-7 checkbox组件示例运行效果图.png)

图7-7 checkbox组件示例运行效果图




