#7-7-1 canvas
canvas画布组件，可用于画出任意形状，实现页面动画，
canvas所包含的属性：

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| canvas-id | String |  | canvas 组件的唯一标识符 |
| disable-scroll | Boolean | false | 当在 canvas 中移动时，禁止屏幕滚动以及下拉刷新 |
| bindtouchstart | EventHandle |  | 手指触摸动作开始 |
| bindtouchmove | EventHandle |  | 手指触摸后移动 |
| bindtouchend | EventHandle |  | 手指触摸动作结束 |
| bindtouchcancel | EventHandle |  | 手指触摸动作被打断，如来电提醒，弹窗 |
| bindlongtap | EventHandle |  | 手指长按 500ms 之后触发，触发了长按事件后进行移动不会触发屏幕的滚动 |
| binderror | EventHandle |  | 当发生错误时触发 error 事件，detail = {errMsg: 'something wrong'} |



**注意:**

* canvas 组件是由客户端创建的原生组件，它的层级是最高的。
* 请勿在 scroll-view 中使用 canvas 组件。
* css 动画对 canvas 组件无效。



