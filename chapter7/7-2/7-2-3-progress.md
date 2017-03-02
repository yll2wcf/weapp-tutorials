# 7.2.3 progress

progress 进度条，开发者可以通过改变属性来控制进度条样式。  
progress 包含的属性，如表7-8所示：

表7-8

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| percent | Float |  | 百分比0~100 |
| show-info | Boolean | false | 在进度条右侧显示百分比 |
| stroke-width | Number | 6 | 进度条线的宽度，单位px |
| color | Color | \#09BB07 | 进度条颜色 |
| active | Boolean | false | 进度条从左往右的动画 |

示例代码：  
wxml中：

```xml
<view class="progress-view">
  <view class="progress-box">
    <progress percent="20" show-info />
  </view>
  <view class="progress-box">
    <progress percent="40" stroke-width="12" />
  </view>
  <view class="progress-box">
    <progress percent="60" color="pink" />
  </view>
  <view class="progress-box">
    <progress percent="100" active />
  </view>
</view>
```

运行效果如图7-6所示：

![](/assets/图7-6 progress组件示例运行效果图.png)

图7-6 progress组件示例运行效果图



