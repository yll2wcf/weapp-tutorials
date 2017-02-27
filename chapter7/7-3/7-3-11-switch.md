#7-3-11 switch
switch 开关选择器。
switch 所包含的属性，如表7-23所示：

表7-23

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| checked | Boolean | false | 是否选中 |
| type | String | switch | 样式，有效值：switch, checkbox |
| bindchange | EventHandle | | checked 改变时触发 change 事件，event.detail={ value:checked} |
| color | Color | | switch 的颜色，同 css 的 color |
示例代码：
wxml中：
```xml
  <view class="switch-view">
    <view>type="switch"</view>
    <view class="switch">
      <switch checked="{{switch1Checked}}" bindchange="switch1Change" />
    </view>
  </view>
  <view class="switch-view">
    <view>type="checkbox"</view>
    <view class="switch">
      <switch type="checkbox" checked="{{switch2Checked}}" bindchange="switch2Change" />
    </view>
  </view>
```
js中：
```js
var pageData = {
  data: {
    switch1Checked: true,
    switch2Checked: false,
    switch1Style: '',
    switch2Style: 'text-decoration: line-through'
  }
}
for(var i = 1; i <= 2; ++i) {
  (function(index) {
    pageData[`switch${index}Change`] = function(e) {
      console.log(`switch${index}发生change事件，携带值为`, e.detail.value)
      var obj = {}
      obj[`switch${index}Checked`] = e.detail.value
      this.setData(obj)
      obj = {}
      obj[`switch${index}Style`] = e.detail.value ? '' : 'text-decoration: line-through'
      this.setData(obj)
    }
  })(i)
}
Page(pageData)
```
运行效果如图7-16所示：

![](/assets/图7-16 switch组件示例运行效果图.png)

图7-16 switch组件示例运行效果图