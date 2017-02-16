#7-3-10 slider
slider 滑块选择器。
slider 所包含的属性：
| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| min | Number | 0 | 最小值 || max | Number | 100 | 最大值 |
| step | Number | 1 | 步长，取值必须大于 0，并且可被\(max - min\)整除 |
| disabled | Boolean | false | 是否禁用 |
| value | Number | 0 | 当前取值 |
| color | Color | \#e9e9e9 | 背景条的颜色 |
| selected-color | Color | \#1aad19 | 已选择的颜色 |
| show-value | Boolean | false | 是否显示当前 value |
| bindchange | EventHandle | | 完成一次拖动后触发的事件，event.detail = {value: value} |
示例代码：
wxml：
```
<view class="slider">
  <text>设置left/right icon</text>
  <slider bindchange="slider1change" left-icon="cancel" right-icon="success_no_circle" />
</view>
<view class="slider">
  <text>设置step</text>
  <slider bindchange="slider2change" step="5" />
</view>
<view class="slider">
  <text>显示当前value</text>
  <slider bindchange="slider3change" show-value/>
</view>
<view class="slider">
  <text>设置最小/最大值</text>
  <slider bindchange="slider4change" min="50" max="200" show-value/>
</view>
```
js中：
```
var pageData = {}
for(var i = 1; i < 5; ++i) {
  (function (index) {
    pageData[`slider${index}change`] = function(e) {
      console.log(`slider${index}发生change事件，携带值为`, e.detail.value)
    }
  })(i);
}
Page(pageData)
```
运行效果如图7-15所示：

![](/assets/图7-15 slider组件示例运行效果图.png)