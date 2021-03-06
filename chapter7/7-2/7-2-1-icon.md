##7.2.1 icon

icon 图标组件，小程序中自带的图标。  
icon 的属性包括，如表7-7所示：

表7-7

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| type | String |  | icon的类型，有效值：success, success\_no\_circle, info, warn, waiting, cancel, download, search, clear |
| size | Number | 23 | icon的大小，单位px |
| color | Color |  | icon的颜色，同css的color |

示例代码：  
wxml中：

```xml
<view class="group">
  <block wx:for="{{iconSize}}">
    <icon type="success" size="{{item}}"/>
  </block>
</view>
<view class="group">
  <block wx:for="{{iconType}}">
    <icon type="{{item}}" size="45"/>
  </block>
</view>
<view class="group">
  <block wx:for="{{iconColor}}">
    <icon type="success" size="45" color="{{item}}"/>
  </block>
</view>
```


运行效果如图7-4所示：

![](/assets/图7-4icon组件示例运行效果图.png)

图7-4 icon组件示例运行效果图