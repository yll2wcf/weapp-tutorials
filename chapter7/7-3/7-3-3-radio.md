# 7-3-3 radio

单选框，为用户提供一系列选项，用户可以选择其中一项。与多选框 checkbox 类似。  
radio-group 单项选择器，内部由多个`<radio/>`组成，如表7-12所示。

表7-12

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| bindchange | EventHandle |  | `<radio-group/>`中的选中项发生变化时触发 change 事件，event.detail = {value: 选中项radio的value} |

radio单选项目，如表7-13所示。

表7-13

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String |  | `<radio/>`标识。当该`<radio/>`选中时，`<radio-group/>`的 change 事件会携带`<radio/>`的value |
| checked | Boolean | false | 当前是否选中 |
| disabled | Boolean | false | 是否禁用 |
| color | Color |  | radio 的颜色，同css的color |

示例代码：  
wxml中：
```xml
<radio-group class="radio-group" bindchange="radioChange">
  <label class="radio">
    <radio value="{{item.value}}" checked="true" />北京
  </label>
  <label class="radio">
    <radio value="{{item.value}}" checked="true" />天津
  </label>
  <label class="radio">
    <radio value="{{item.value}}" checked="true" />上海
  </label>
  <label class="radio">
    <radio value="{{item.value}}" checked="true" />重庆
  </label>
  <label class="radio">
    <radio value="{{item.value}}" checked="true" />深圳
  </label>
  <label class="radio">
    <radio value="{{item.value}}" checked="true" />广州
  </label>
</radio-group>
```
运行效果如图7-9所示：

![](/assets/图7-9 radio组件示例运行效果图.png)

图7-9 radio组件示例运行效果图

