##7.3.6 form

form 表单，将组件内的用户输入的`<switch/>` `<input/>` `<checkbox/>` `<slider/>` `<radio/> ` `<picker/>` 标签提交。  
当点击`<form/>`标签中 formType 为 submit 的`<button/>`组件时，会将表单组件中的 value 值进行提交，需要在表单组件中加上 name 来作为 key。  
form 所包含的属性，如表7-16所示：

表7-16

| 属性名 | 类型 | 说明 |
| :--- | :--- | :--- |
| report-submit | Boolean | 是否返回 formId 用于发送模板消息 |
| bindsubmit | EventHandle | 携带 form 中的数据触发 submit 事件，event.detail = {value : {'name': 'value'} , formId: ''} |
| bindreset | EventHandle | 表单重置时会触发 reset 事件 |


示例代码：
wxml中：
```xml
<view class="page-body">
    <form catchsubmit="formSubmit" catchreset="formReset">
      <view class="page-section page-section-gap">
        <view class="page-section-title">switch</view>
        <switch name="switch"/>
      </view>

      <view class="page-section page-section-gap">
        <view class="page-section-title">radio</view>
        <radio-group name="radio">
          <label><radio value="radio1"/>选项一</label>
          <label><radio value="radio2"/>选项二</label>
        </radio-group>
      </view>

      <view class="page-section page-section-gap">
        <view class="page-section-title">checkbox</view>
        <checkbox-group name="checkbox">
          <label><checkbox value="checkbox1"/>选项一</label>
          <label><checkbox value="checkbox2"/>选项二</label>
        </checkbox-group>
      </view>

      <view class="page-section page-section-gap">
        <view class="page-section-title">slider</view>
        <slider value="50" name="slider" show-value ></slider>
      </view>

      <view class="page-section">
        <view class="page-section-title">input</view>
        <view class="weui-cells weui-cells_after-title">
          <view class="weui-cell weui-cell_input">
            <view class="weui-cell__bd">
              <input class="weui-input" name="input" placeholder="这是一个输入框" />
            </view>
          </view>
        </view>
      </view>

      <view class="btn-area">
        <button type="primary" formType="submit">Submit</button>
        <button formType="reset">Reset</button>
      </view>
    </form>
  </view>
```
js中：
```js
Page({
  data: {
    pickerHidden: true,
    chosen: ''
  },
  pickerConfirm: function (e) {
    this.setData({
      pickerHidden: true
    })
    this.setData({
      chosen: e.detail.value
    })
  },
  pickerCancel: function (e) {
    this.setData({
      pickerHidden: true
    })
  },
  pickerShow: function (e) {
    this.setData({
      pickerHidden: false
    })
  },
  formSubmit: function (e) {
    console.log('form发生了submit事件，携带数据为：', e.detail.value)
  },
  formReset: function (e) {
    console.log('form发生了reset事件，携带数据为：', e.detail.value)
    this.setData({
      chosen: ''
    })
  }
})
```

运行效果如图7-12所示：

![](/assets/图7-12form组件示例运行效果图.png)

图7-12 form组件示例运行效果图


