#wx.onSocketError
wx.onSocketError(CALLBACK)
监听WebSocket错误。
示例代码：
```js
wx.connectSocket({
  url: 'test.php'
})
wx.onSocketOpen(function(res){
  console.log('WebSocket连接已打开！')
})
wx.onSocketError(function(res){
  console.log('WebSocket连接打开失败，请检查！')
})
```

