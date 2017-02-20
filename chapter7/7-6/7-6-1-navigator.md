#7-6-1 navigator
navigator 导航组件，类似于HTML中的&lt; a>标签，但无target属性，默认跳转到新页面，redirect为在当前页面打开。

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| url | String |  | 应用内的跳转链接 |
| redirect | Boolean | false | 打开方式为页面重定向，对应 wx.redirectTo（将被废弃，推荐使用 open-type） |
| open-type | String | navigate | 可选值 'navigate'、'redirect'、'switchTab'，对应于wx.navigateTo、wx.redirectTo、wx.switchTab的功能 |
| hover-class | String | navigator-hover | 指定点击时的样式类，当hover-class="none"时，没有点击态效果 |
| hover-start-time | Number | 50 | 按住后多久出现点击态，单位毫秒 |
| hover-stay-time | Number | 600 | 手指松开后点击态保留时间，单位毫秒 |


**注意**：navigator-hover 默认为 {background-color: rgba(0, 0, 0, 0.1); opacity: 0.7;}, &lt; navigator/> 的子节点背景色应为透明色。

示例代码：
