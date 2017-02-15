# 7-1-2 scroll-view

scroll-view组件，它用来定义一个可滚动的视图区域，相当于ios开发中的UIScrollView。里面的内容如果超过这个区域的宽或高时，就会出现滚动条。  
scroll-view包含的属性：

| 属性名 | 类型 | 默认值 | 注释 |
| :--- | :--- | :--- | :--- |
| scroll-x | Boolean | false | 允许横向滚动 |
| scroll-y | Boolean | false | 允许纵向滚动 |
| upper-threshold | Number | 50 | 距顶部/左边多远时（单位px），触发 scrolltoupper 事件 |
| lower-threshold | Number | 50 | 距底部/右边多远时（单位px），触发 scrolltolower 事件 |
| scroll-top | Number |  | 设置竖向滚动条位置 |
| scroll-left | Number |  | 设置横向滚动条位置 |
| scroll-into-view | String |  | 值应为某子元素id，则滚动到该元素，元素顶部对齐滚动区域顶部 |
| bindscrolltoupper | EventHandle |  | 滚动到顶部/左边，会触发 scrolltoupper 事件 |
| bindscrolltolower | EventHandle |  | 滚动到底部/右边，会触发 scrolltolower 事件 |
| bindscroll | EventHandle |  | 滚动时触发，event.detail = {scrollLeft, scrollTop, scrollHeight, scrollWidth, deltaX, deltaY} |




