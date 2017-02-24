##### wx.switchTab(OBJECT)

跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面

OBJECT 参数说明：

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
|url	|String	|是	|需要跳转的 tabBar 页面的路径（需在 app.json 的 tabBar 字段定义的页面），路径后不能带参数|
|success	|Function	|否	|接口调用成功的回调函数|
|fail	|Function	|否	|接口调用失败的回调函数|
|complete	|Function	|否	|接口调用结束的回调函数（调用成功、失败都会执行）|
示例代码：
```json
//定义在app.json里设置页面底部的选项卡
{
  "tabBar": {
    "list": [{
      "pagePath": "index",
      "text": "首页"
    },{
      "pagePath": "other",
      "text": "其他"
    }]
  }
}
```
```
//调用API切换选项卡
wx.switchTab({
  url: '/index'
})
```
注意wx.navigateTo和wx.redirectTo不允许跳转到tabbar页面，只能用wx.switchTab跳转到tabbar页面。