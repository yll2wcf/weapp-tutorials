# 7-3-3 radio

单选框，为用户提供一系列选项，用户可以选择其中一项。与多选框checkbox类似。  
radio-group单项选择器，内部由多个&lt; radio/&gt;组成。

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| bindchange | EventHandle |  | &lt; radio-group/&gt; 中的选中项发生变化时触发 change 事件，event.detail = {value: 选中项radio的value} |

radio单选项目。

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String |  | &lt; radio/&gt; 标识。当该&lt; radio/&gt; 选中时，&lt; radio-group/&gt; 的 change 事件会携带&lt; radio/&gt;的value |
| checked | Boolean | false | 当前是否选中 |
| disabled | Boolean | false | 是否禁用 |
| color | Color |  | radio的颜色，同css的color |

示例代码：  
wxml中：
```
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



