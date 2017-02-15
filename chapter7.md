# 第七章 组件的开发应用

小程序为开发者提供了一系列功能丰富的基础组件，开发者可以对这些组件进行组合，从而进行快速开发，创建出各式各样的小程序。组件是视图层的基本元素，是构建页面的基础。组件不仅自带一些功能，还能有微信风格的样式。一个组件通常包括开始标签、结束标签、属性、内容。属性用来修饰该组件，内容放在开始标签和结束标签之间，用来页面显示。

```
<tagname property="value">
  Content goes here ...
</tagename>
```

注意：所有组件与属性都是小写，以连字符-连接

### 共同属性类型

所有组件共有的属性：

| 属性名 | 类型 | 描述 | 注释 |
| --- | :---: | --- | --- |
| id | String | 组件的唯一标示 | 保持整个页面唯一 |
| class | String | 组件的样式类 | 在对应的 WXSS 中定义的样式类 |
| style | String | 组件的内联样式 | 可以动态设置的内联样式 |
| hidden | Boolean | 组件是否显示 | 所有组件默认显示 |
| data-\* | Any | 自定义属性 | 组件上触发的事件时，会发送给事件处理函数 |
| bind\*/catch\* | EventHandler | 组件的事件 |  |

### 特殊属性

每个组件都有自定义的属性，可以对功能样式进行修改，但只支持以下七种数据类型：

| 类型 | 描述 | 注释 |
| :--- | :--- | :--- |
| Boolean | 布尔值 | 组件写上该属性，不管该属性等于什么，其值都为true，只有组件上没有写该属性时，属性值才为false。如果属性值为变量，变量的值会被转换为Boolean类型 |
| Number | 数字 | 1, 2.5 |
| String | 字符串 | "string" |
| Array | 数组 | \[ 1, "string" \] |
| Object | 对象 | { key: value } |
| EventHandler | 事件处理函数名 | "handlerName" 是 Page中定义的事件处理函数名 |
| Any | 任意属性 |  |

### 组件

微信小程序为开发者提供七类基础组件：

| 类别 | 包含组件 | 说明 |
| :--- | :--- | :--- |
| 视图容器\(View Container\) | view、scroll-view、swiper | 视图、可滚动视图、滑块视图 |
| 基础内容\(Basic Content\) | icon、text、progress | 图标、文字、进度条 |
| 表单\(Form\) | button、form、input、checkbox、radio、picker、picker-view、slider、switch、label | 构建表单的基础组件 |
| 多媒体\(Media\) | audio、image、video | 音频、图片、视频 |
| 地图\(Map\) | map | 地图 |
| 导航\(Navigation\) | navigator | 页面导航 |
| 画布\(Canvas\) | canvas | 画布 |

开发者通过这些组件，就可以完美的构建出自己的微信小程序。我们将在本章详细阐述这七类组件的开发及使用方法。

