# 7-2-2 text

text文本组件，显示文字时使用的组件，类似于HTML中的&lt; span>标签，支持“\n”换行，&lt; text>组件内只支持&lt; text>嵌套。同时&lt; text>是唯一可复制文本的标签。  
**注意**：除了文本节点以外的其他节点都无法长按选中。但是，目前版本的text长按复制功能尚未实现。

示例代码：  
wxml中：

```xml
<view class="btn-area">
  <view class="body-view">
    <text>{{text}}</text>
    <button bindtap="add">add line</button>
    <button bindtap="remove">remove line</button>
  </view>
</view>
```

js中

```js
var initData = '我是第一行\n我是第二行\n我是第三行'
var extraLine = [];
Page({
  data: {
    text: initData
  },
  add: function(e) {
    extraLine.push('下一行')
    this.setData({
      text: initData + '\n' + extraLine.join('\n')
    })
  },
  remove: function(e) {
    if (extraLine.length > 0) {
      extraLine.pop()
      this.setData({
        text: initData + '\n' + extraLine.join('\n')
      })
    }
  }
})
```

运行效果如图7-5所示：

![](/assets/图7-5 text组件示例运行效果图.png)

图7-5 text组件示例运行效果图



