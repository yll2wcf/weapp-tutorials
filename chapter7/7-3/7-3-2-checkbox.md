# 7-3-2 checkbox

复选框,为用户提供一系列选项，用户可以选择多个。  
checkbox-group多项选择器，内部由多个checkbox组成，如表7-10所示。

表7-10

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| bindchange | EventHandle |  | checkbox-group中选中项发生改变是触发 change 事件，detail = {value:\[选中的checkbox的value的数组\]} |

checkbox多选项目，如表7-11所示。

表7-11

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String |  | &lt; checkbox/&gt;标识，选中时触发&lt; checkbox-group/&gt;的 change 事件，并携带 &lt; checkbox/&gt; 的 value |
| disabled | Boolean | false | 是否禁用 |
| checked | Boolean | false | 当前是否选中，可用来设置默认选中 |
| color | Color |  | checkbox的颜色，同css的color |

示例代码：  
wxml中：

```xml
<view class="container">
  <template is="head" data="{{title: 'checkbox'}}" />
  <view class="page-section-title">多选框默认样式
  </view>
  <label class="checkbox">
    <checkbox value="cb" checked="true" />项目一
  </label>
  <label class="checkbox">
    <checkbox value="cb" />项目二
  </label>
  <label class="checkbox">
    <checkbox value="cb" />项目三
  </label>
  <label class="checkbox">
    <checkbox value="cb" />项目四
  </label>
  <label class="checkbox">
    <checkbox value="cb" />项目五
  </label>
  <label class="checkbox">
    <checkbox value="cb" />项目六
  </label>
  <template is="foot" />
</view>
```

运行效果如图7-8所示：

![](/assets/图7-8 button组件示例运行效果图.png)


