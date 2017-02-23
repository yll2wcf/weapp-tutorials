##### wx.showModal(OBJECT)

显示模拟弹窗，即带交互按钮的提示框。

OBJECT参数说明：

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
|title	|String	|是	|提示的标题|
|content	|String	|是	|提示的内容|
|showCancel	|Boolean	|否	|是否显示取消按钮，默认为 true|
|cancelText	|String	|否	|取消按钮的文字，默认为"取消"，最多 4 个字符|
|cancelColor	|HexColor	|否	|取消按钮的文字颜色，默认为"#000000"|
|confirmText	|String	|否	|确定按钮的文字，默认为"确定"，最多 4 个字符|
|confirmColor	|HexColor	|否	|确定按钮的文字颜色，默认为"#3CC51F"|
|success	|Function	|否	|接口调用成功的回调函数，返回res.confirm为true时，表示用户点击确定按钮|
|fail	|Function	|否	|接口调用失败的回调函数|
|complete	|Function	|否	|接口调用结束的回调函数（调用成功、失败都会执行）|

示例代码：

```xml
<button type="default" bindtap="modalTap">点击弹出MODAL</button>
```

```js
modalTap: function () {
    wx.showModal({
      //title: "标题",
      content: "弹窗内容，告知当前状态、信息和解决方法，描述文字尽量控制在三行内",
      //showCancel: false,
      confirmText: "确定",
      cancelText: "取消",
      //confirmColor: "#66ccff",
      //cancelColor: "ffcc66"
    })
  },
```

运行结果（图8-7-2）：
![](/assets/8-7-2.png)图8-7-2

