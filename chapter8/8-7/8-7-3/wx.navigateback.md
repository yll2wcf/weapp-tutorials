###wx.navigateBack(OBJECT)

关闭当前页面，返回上一页面或多级页面。可通过 getCurrentPages()) 获取当前的页面栈，决定需要返回几层。

OBJECT 参数说明（表8-62）：
表8-62

| 参数 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
|delta	|Number	|1	|返回的页面数，如果 delta 大于现有页面数，则返回到首页。|

示例代码：
```js
// 注意：调用 navigateTo 跳转时，调用该方法的页面会被加入堆栈，而 redirectTo 方法则不会。见下方示例代码

// 此处是A页面
wx.navigateTo({
  url: 'B?id=1'
})

// 此处是B页面
wx.navigateTo({
  url: 'C?id=1'
})

// 在C页面内 navigateBack，将返回A页面
wx.navigateBack({
  delta: 2
})
```

使用navigateBack可以使用户一次后退多个页面，参数delta的值表示了要后退页面的个数（也就是页面从栈里出栈的个数）。

这个方法会使我们的页面跳转更灵活，尤其是像返回首页这种功能，使用navigateBack很容易实现。如果当前页面的层数不容易计算或层数为动态值，我们可以先用getCurrentPages()来获取当前栈里有多少个页面，然后再调用navigateBack。