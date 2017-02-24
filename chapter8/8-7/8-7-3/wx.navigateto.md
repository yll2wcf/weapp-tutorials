##### wx.navigateTo(OBJECT)

保留当前页面，跳转到应用内的某个页面，使用wx.navigateBack可以返回到原页面。

OBJECT 参数说明：

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
|url	|String	|是	|需要跳转的应用内非 tabBar 的页面的路径 , 路径后可以带参数。参数与路径之间使用?分隔，参数键与参数值用=相连，不同参数用&分隔；如 'path?key=value&key2=value2'|
|success	|Function	|否	|接口调用成功的回调函数|
|fail	|Function	|否	|接口调用失败的回调函数|
|complete	|Function	|否	|接口调用结束的回调函数（调用成功、失败都会执行）|

示例代码：
```js
//准备开始跳转的页面
wx.navigateTo({
  url: 'test?id=1'
})
```
```js
//跳转到的页面，通过下面的方法会获得跳转中携带的参数“id=1”
Page({
  onLoad: function(option){
    console.log(option.query)
  }
})
```

注意：为了不让用户在使用小程序时造成困扰，我们规定页面路径只能是五层，请尽量避免多层级的交互方式。

从原理上讲，小程序的页面是由栈管理的。栈就像一个盒子（如图8-7-6所示）：

![](/assets/8-7-6.png)图8-7-6

这里面的a1..an就是我们的页面，a1为首页，每次使用navigateTo，就会有新的页面（依次为a2，a3...）加入到这个盒子中。对于小程序而言，当我们向盒子里加入了a5之后（即连续调用了4次navigateTo），再调用navigateTo的话就会失败。一般情况下我们的小程序不会出现这种问题，只有非常复杂的小程序需要注意这一点，解决这个问题的方法是使用下面要介绍的redirectTo代替navigateTo来实现页面跳转。