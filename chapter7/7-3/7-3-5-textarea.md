#7-3-5 textarea
textarea多行输入框，与input类似，相当于文本编辑器，可以输入多行文字。


**注意：**
* 微信版本 6.3.30，textarea 在列表渲染时，新增加的 textarea 在自动聚焦时的位置计算错误。
* textarea 的 blur 事件会晚于页面上的 tap 事件，如果需要在 button 的点击事件获取 textarea，可以使用 form 的 bindsubmit。
* 不建议在多行文本上对用户的输入进行修改，所以 textarea 的 bindinput 处理函数并不会将返回值反映到 textarea 上。
* textarea 组件是由客户端创建的原生组件，它的层级是最高的。
* 请勿在 scroll-view 中使用 textarea 组件。
* css 动画对 textarea 组件无效。




