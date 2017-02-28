#wx.sendSocketMessage
wx.sendSocketMessage(OBJECT)
通过 WebSocket 连接发送数据，需要先 wx.connectSocket，并在 wx.onSocketOpen 回调之后才能发送。
OBJECT参数说明，如表8-7所示：

表8-7

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| data | String/ArrayBuffer | 是 | 需要发送的内容 |
| success | Function | 否 | 接口调用成功的回调函数 |
| fail | Function | 否 | 接口调用失败的回调函数 |
| complete | Function | 否 | 接口调用结束的回调函数（调用成功、失败都会执行）|


示例代码：
```js
var socketOpen = false
var socketMsgQueue = []
wx.connectSocket({
  url: 'test.php'
})

wx.onSocketOpen(function(res) {
  socketOpen = true
  for (var i = 0; i < socketMsgQueue.length; i++){
     sendSocketMessage(socketMsgQueue[i])
  }
  socketMsgQueue = []
})

function sendSocketMessage(msg) {
  if (socketOpen) {
    wx.sendSocketMessage({
      data:msg
    })
  } else {
     socketMsgQueue.push(msg)
  }
}
```

