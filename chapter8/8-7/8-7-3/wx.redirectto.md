##### wx.redirectTo(OBJECT)

关闭当前页面，跳转到应用内的某个页面。

OBJECT 参数说明：

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
|url	|String	|是	|需要跳转的应用内非 tabBar 的页面的路径，路径后可以带参数。参数与路径之间使用?分隔，参数键与参数值用=相连，不同参数用&分隔；如 'path?key=value&key2=value2'|
|success	|Function	|否	|接口调用成功的回调函数|
|fail	|Function	|否	|接口调用失败的回调函数|
|complete	|Function	|否	|接口调用结束的回调函数（调用成功、失败都会执行）|

示例代码：
```js
wx.redirectTo({
  url: 'test?id=1'
})
```

redirectTo的用法与navigateTo的用法一样，这两者的区别在于navigateTo在调用时将新页面入栈，而使用redirectTo会先将当前页面出栈（即关闭当前页面）再将新的页面入栈并打开。所以使用redirectTo不会导致小程序页面的层数增长，也就不会导致页面层数超过5层。

使用redirectTo与navigateTo的区别还在于用户在页面跳转之后点击返回，例如我们从首页（index）使用navigateTo跳转到页面A，然后再调用navigateTo到页面B，这时点击返回，页面B出栈，当前显示的页面返回到跳转前的页面A。而如果我们在页面A使用redirectTo跳转到页面B，这时点击返回，因为页面A已经被出栈了，所以页面会返回到首页上，这在一定程度上会导致用户的混乱。因此建议在进行页面跳转的时候，尽可能使用navigateTo，只有在特定情况或页面层数超过5层再考虑使用redirectTo。