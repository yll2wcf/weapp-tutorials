# 7-3-8 picker

picker滚动选择器，从底部弹出，现支持三种样式，通过mode来区分，分别是普通选择器，时间选择器，日期选择器，默认是普通选择器（mode = selector）。  
普通选择器（mode = selector）所包含的属性，如表7-18所示：

表7-18

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| range | Array / Object Array | \[\] | mode为 selector 时，range 有效 |
| range-key | String |  | 当 range 是一个 Object Array 时，通过 range-key 来指定 Object 中 key 的值作为选择器显示内容 |
| value | Number | 0 | value 的值表示表示选择了 range 中的第几个（下标从 0 开始）。 |
| bindchange | EventHandle |  | value 改变时触发 change 事件，event.detail = {value: value} |
| disabled | Boolean | false | 是否禁用 |

时间选择器（mode = time）所包含的属性，如表7-19所示：

表7-19

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String |  | 表示选中的时间，格式为"hh:mm" |
| start | String |  | 表示有效时间范围的开始，字符串格式为"hh:mm" |
| end | String |  | 表示有效时间范围的结束，字符串格式为"hh:mm" |
| bindchange | EventHandle |  | value 改变时触发 change 事件，event.detail = {value: value} |
| disabled | Boolean | false | 是否禁用 |

日期选择器（mode = date）所包含的属性，如表7-20所示：

表7-20

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String | 0 | 表示选中的日期，格式为"YYYY-MM-DD" |
| start | String |  | 表示有效日期范围的开始，字符串格式为"YYYY-MM-DD" |
| end | String |  | 表示有效日期范围的结束，字符串格式为"YYYY-MM-DD" |
| fields | String | day | 有效值 year,month,day，表示选择器的粒度 |
| bindchange | EventHandle |  | value 改变时触发 change 事件，event.detail = {value: value} |
| disabled | Boolean | false | 是否禁用 |


示例代码：
wxml中：
```xml
<view class="picker-view">
  <view>地区选择器</view>
  <picker bindchange="bindPickerChange" value="{{index}}" range="{{array}}">
    <view class="picker-wrp">当前选择：{{array[index]}}</view>
  </picker>
</view>
<view class="picker-view">
  <view>时间选择器</view>
  <picker mode="time" value="{{time}}" start="09:01" end="21:01" bindchange="bindTimeChange">
    <view class="picker-wrp">当前选择: {{time}}</view>
  </picker>
</view>

<view class="picker-view">
  <view>日期选择器</view>
  <picker mode="date" value="{{date}}" start="2015-09-01" end="2017-09-01" bindchange="bindDateChange">
    <view class="picker-wrp">当前选择: {{date}}</view>
  </picker>
</view>
```
js中：
```js
Page({
  data: {
    array: ['美国', '中国', '巴西', '日本'],
    objectArray: [
      {
        id: 0,
        name: '美国'
      },
      {
        id: 1,
        name: '中国'
      },
      {
        id: 2,
        name: '巴西'
      },
      {
        id: 3,
        name: '日本'
      }
    ],
    index: 0,
    date: '2016-09-01',
    time: '12:01'
  },
  bindPickerChange: function(e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      index: e.detail.value
    })
  },
  bindDateChange: function(e) {
    this.setData({
      date: e.detail.value
    })
  },
  bindTimeChange: function(e) {
    this.setData({
      time: e.detail.value
    })
  }
})
```

运行效果如图7-14所示：

![](/assets/图7-14 picker组件示例运行效果图.png)

图7-14 picker组件示例运行效果图




