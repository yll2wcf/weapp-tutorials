#wx.onSocketOpen
wx.onSocketOpen(CALLBACK)
监听WebSocket连接打开事件。
示例代码：
```js
wx.connectSocket({
  url: 'test.php'
})
wx.onSocketOpen(function(res) {
  console.log('WebSocket连接已打开！')
})
```


