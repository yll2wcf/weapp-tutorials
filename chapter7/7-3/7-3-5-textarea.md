##7.3.5 textarea

textarea 多行输入框，与input类似，相当于文本编辑器，可以输入多行文字。
textarea 所包含的属性，如表7-15所示：

表7-15

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String |  | 输入框的内容 |
| placeholder | String |  | 输入框为空时占位符 |
| placeholder-style | String |  | 指定 placeholder 的样式 |
| placeholder-class | String | textarea-placeholder | 指定 placeholder 的样式类 |
| disabled | Boolean | false | 是否禁用 |
| maxlength | Number | 140 | 最大输入长度，设置为 -1 的时候不限制最大长度 |
| auto-focus | Boolean | false | 自动聚焦，拉起键盘。 |
| focus | Boolean | false | 获取焦点 |
| auto-height | Boolean | false | 是否自动增高，设置auto-height时，style.height不生效 |
| fixed | Boolean | false | 如果 textarea 是在一个`position:fixed`的区域，需要显示指定属性 fixed 为 true |
| cursor-spacing | Number | 0 | 指定光标与键盘的距离，单位 px 。取 textarea 距离底部的距离和 cursor-spacing 指定的距离的最小值作为光标与键盘的距离 |
| bindfocus | EventHandle |  | 输入框聚焦时触发，event.detail = {value: value} |
| bindblur | EventHandle |  | 输入框失去焦点时触发，event.detail = {value: value} |
| bindlinechange | EventHandle |  | 输入框行数变化时调用，event.detail = {height: 0, heightRpx: 0, lineCount: 0} |
| bindinput | EventHandle |  | 当键盘输入时，触发 input 事件，event.detail = {value: value}， **bindinput 处理函数的返回值并不会反映到 textarea 上** |
| bindconfirm | EventHandle |  | 点击完成时， 触发 confirm 事件，event.detail = {value: value} |

示例代码：
wxml中：
```xml
<view class="container">
  <template is="head" data="{{title: 'textarea'}}" />
  <view class="textarea-view">
    <view>输入区域高度自适应，不会出现滚动条</view>
    <view class="textarea-wrp">
      <textarea bindblur="bindTextAreaBlur" auto-height />
    </view>
  </view>
  <view class="textarea-view">
    <view>这是一个可以自动聚焦的textarea</view>
    <view class="textarea-wrp">
      <textarea auto-focus="true" style="height: 3em" />
    </view>
  </view>
  <template is="foot" />
</view>
```
js中：
```js
Page({
  data: {
    focus: false
  },
  bindTextAreaBlur: function(e) {
    console.log(e.detail.value)
  }
})
```

运行效果如图7-11所示：

![](/assets/图7-11 textarea组件示例运行效果图.png)

图7-11 textarea组件示例运行效果图


**注意：**

* 微信版本 6.3.30，textarea 在列表渲染时，新增加的 textarea 在自动聚焦时的位置计算错误。
* textarea 的 blur 事件会晚于页面上的 tap 事件，如果需要在 button 的点击事件获取 textarea，可以使用 form 的 bindsubmit。
* 不建议在多行文本上对用户的输入进行修改，所以 textarea 的 bindinput 处理函数并不会将返回值反映到 textarea 上。
* textarea 组件是由客户端创建的原生组件，它的层级是最高的。
* 请勿在 scroll-view 中使用 textarea 组件。
* css 动画对 textarea 组件无效。



