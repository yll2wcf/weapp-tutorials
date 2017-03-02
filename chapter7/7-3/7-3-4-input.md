##7.3.4 input

input 输入框，类似于一个文本编辑器，用来和用户进行文本交互。  
input 所包含的属性，如表7-14所示：

表7-14

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String |  | 输入框的初始内容 |
| type | String | text | input 的类型，有效值：text, number, idcard, digit |
| password | Boolean | false | 是否是密码类型 |
| placeholder | String |  | 输入框为空时占位符 |
| placeholder-style | String |  | 指定 placeholder 的样式 |
| placeholder-class | String | input-placeholder | 指定 placeholder 的样式类 |
| disabled | Boolean | false | 是否禁用 |
| maxlength | Number | 140 | 最大输入长度，设置为 -1 的时候不限制最大长度 |
| cursor-spacing | Number | 0 | 指定光标与键盘的距离，单位 px 。取 input 距离底部的距离和 cursor-spacing 指定的距离的最小值作为光标与键盘的距离 |
| auto-focus | Boolean | false | \(即将废弃，请直接使用 focus \)自动聚焦，拉起键盘 |
| focus | Boolean | false | 获取焦点 |
| bindinput | EventHandle |  | 当键盘输入时，触发input事件，event.detail = {value: value}，处理函数可以直接 return 一个字符串，将替换输入框的内容。 |
| bindfocus | EventHandle |  | 输入框聚焦时触发，event.detail = {value: value} |
| bindblur | EventHandle |  | 输入框失去焦点时触发，event.detail = {value: value} |
| bindconfirm | EventHandle |  | 点击完成按钮时触发，event.detail = {value: value} |

示例代码：  
wxml中：

```xml
<view class="container">
  <template is="head" data="{{title: 'input'}}" />
  <view class="page-section">
    <view>可以自动聚焦的input</view>
    <view class="weui-cells">
      <input class="weui-input" auto-focus placeholder="将会获取焦点" />
    </view>
  </view>
  <view class="page-section">
    <view>控制最大输入长度的input</view>
    <view class="weui-cells">
      <input class="weui-input" maxlength="10" placeholder="最大输入长度为10" />
    </view>
  </view>
  <view class="page-section">
    <view>实时获取输入值：{{inputValue}}</view>
    <view class="weui-cells">
      <input class="weui-input" maxlength="10" bindinput="bindKeyInput" placeholder="输入同步到view中" />
    </view>
  </view>
  <view class="page-section">
    <view>控制输入的input</view>
    <view class="weui-cells">
      <input class="weui-input" bindinput="bindReplaceInput" placeholder="连续的两个1会变成2" />
    </view>
  </view>
  <view class="page-section">
    <view>控制键盘的input</view>
    <view class="weui-cells">
      <input class="weui-input" bindinput="bindHideKeyboard" placeholder="输入123自动收起键盘" />
    </view>
  </view>
  <view class="page-section">
    <view>数字输入的input</view>
    <view class="weui-cells">
      <input class="weui-input" type="number" placeholder="这是一个数字输入框" />
    </view>
  </view>
  <view class="page-section">
    <view>密码输入的input</view>
    <view class="weui-cells">
      <input class="weui-input" password type="text" placeholder="这是一个密码输入框" />
    </view>
  </view>
  <view class="page-section">
    <view>带小数点的input</view>
    <view class="weui-cells">
      <input class="weui-input" type="digit" placeholder="带小数点的数字键盘" />
    </view>
  </view>
  <view class="page-section">
    <view>身份证输入的input</view>
    <view class="weui-cells">
      <input class="weui-input" type="idcard" placeholder="身份证输入键盘" />
    </view>
  </view>
  <view class="page-section">
    <view>控制占位符颜色的input</view>
    <view class="weui-cells">
      <input class="weui-input" placeholder-style="color:#F76260" placeholder="占位符字体是红色的" />
    </view>
  </view>
  <template is="foot" />
</view>
```

js中：

```js
Page({
  data: {
    focus: false,
    inputValue: ''
  },
  bindKeyInput: function (e) {
    this.setData({
      inputValue: e.detail.value
    })
  },
  bindReplaceInput: function (e) {
    var value = e.detail.value
    var pos = e.detail.cursor
    var left
    if (pos !== -1) {
      // 光标在中间
      left = e.detail.value.slice(0, pos)
      // 计算光标的位置
      pos = left.replace(/11/g, '2').length
    }

    // 直接返回对象，可以对输入进行过滤处理，同时可以控制光标的位置
    return {
      value: value.replace(/11/g, '2'),
      cursor: pos
    }

    // 或者直接返回字符串,光标在最后边
    // return value.replace(/11/g,'2'),
  },
  bindHideKeyboard: function (e) {
    if (e.detail.value === '123') {
      // 收起键盘
      wx.hideKeyboard()
    }
  }
})
```
wxss中：
```css
.container {
background-color: lightgrey;

}
.page-section{
  margin-bottom: 20rpx;
  width: 100%;
  
}
.weui-cells {
  position: relative;
  margin-top: 1.17647059em;
  background-color: #FFFFFF;
  line-height: 1.41176471;
  font-size: 17px;
}
.weui-input {
  height: 2.58823529em;
  min-height: 2.58823529em;
  line-height: 2.58823529em;
}
```

运行效果如图7-10所示：

![](/assets/图7-10input组件示例运行效果图.png)

图7-10 input组件示例运行效果图

**注意：**
* 微信版本 6.3.30, focus 属性设置无效。
* 微信版本 6.3.30, placeholder 在聚焦时出现重影问题。
* input 组件是一个 native 组件，字体是系统字体，所以无法设置 font-family。
* 在 input 聚焦期间，避免使用 css 动画。

