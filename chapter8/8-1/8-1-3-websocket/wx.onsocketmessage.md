#wx.onSocketMessage
wx.onSocketMessage(CALLBACK)
监听WebSocket接受到服务器的消息事件。
CALLBACK返回参数，如表8-8所示：

表8-8

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| data | String/ArrayBuffer | 服务器返回的消息 |

示例代码：
```js
wx.connectSocket({
  url: 'test.php'
})

wx.onSocketMessage(function(res) {
  console.log('收到服务器内容：' + res.data)
})
```

