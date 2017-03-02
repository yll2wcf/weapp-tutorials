##7.3.7 label

label 用来改进表单组件的可用性，使用`for`属性找到对应的`id`，或者将控件放在该标签下，当点击时，就会触发对应的控件。  
`for`优先级高于内部控件，内部有多个控件的时候默认触发第一个控件。  
目前可以绑定的控件有：`<button/>`, `<checkbox/>`, `<radio/>`, `<switch/>`组件。  
label 只包含一个`for`属性，如表7-17所示：

表7-17

| 属性名 | 类型 | 说明 |
| :--- | :--- | :--- |
| for | String | 绑定控件的 id |

示例代码：
wxml中：
```xml
 <view class="page-body">
    <view class="page-section page-section-gap">
      <view class="page-section-title">表单组件在label内</view>
      <checkbox-group class="group" bindchange="checkboxChange">
        <view class="label-1" wx:for="{{checkboxItems}}">
          <label>
            <checkbox value="{{item.name}}" checked="{{item.checked}}"></checkbox>
            <text class="label-1-text">{{item.value}}</text>
          </label>
        </view>
      </checkbox-group>
    </view>

    <view class="page-section page-section-gap">
      <view class="page-section-title">label用for标识表单组件</view>
      <radio-group class="group" bindchange="radioChange">
        <view class="label-2" wx:for="{{radioItems}}">
          <radio id="{{item.name}}" value="{{item.name}}" checked="{{item.checked}}"></radio>
          <label class="label-2-text" for="{{item.name}}"><text>{{item.name}}</text></label>
        </view>
      </radio-group>
    </view>

    <view class="page-section page-section-gap">
      <view class="page-section-title">label内有多个时选中第一个</view>
      <label class="label-3">
        <checkbox class="checkbox-3">选项一</checkbox>
        <checkbox class="checkbox-3">选项二</checkbox>
      </label>
    </view>
  </view>
```
js中：
```js
Page({
  data: {
    checkboxItems: [
      {name: 'USA', value: '美国'},
      {name: 'CHN', value: '中国', checked: 'true'}
    ],
    radioItems: [
      {name: 'USA', value: '美国'},
      {name: 'CHN', value: '中国', checked: 'true'}
    ],
    hidden: false
  },
  checkboxChange: function (e) {
    var checked = e.detail.value
    var changed = {}
    for (var i = 0; i < this.data.checkboxItems.length; i++) {
      if (checked.indexOf(this.data.checkboxItems[i].name) !== -1) {
        changed['checkboxItems[' + i + '].checked'] = true
      } else {
        changed['checkboxItems[' + i + '].checked'] = false
      }
    }
    this.setData(changed)
  },
  radioChange: function (e) {
    var checked = e.detail.value
    var changed = {}
    for (var i = 0; i < this.data.radioItems.length; i ++) {
      if (checked.indexOf(this.data.radioItems[i].name) !== -1) {
        changed['radioItems[' + i + '].checked'] = true
      } else {
        changed['radioItems[' + i + '].checked'] = false
      }
    }
    this.setData(changed)
  },
  tapEvent: function (e) {
    console.log('按钮被点击')
  }
})
```
运行效果如图7-13所示：

![](/assets/图7-13 label组件示例运行效果图.png)

图7-13 label组件示例运行效果图


