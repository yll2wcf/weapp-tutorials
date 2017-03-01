# 8-1-3 WebSocket 

####wx.connectSocket
wx.connectSocket(OBJECT)
创建一个 WebSocket 连接；一个微信小程序同时只能有一个 WebSocket 连接，如果当前已存在一个 WebSocket 连接，会自动关闭该连接，并重新创建一个 WebSocket 连接。
OBJECT参数说明，如表8-6所示：

表8-6

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| url | String | 是 | 开发者服务器接口地址，必须是 wss 协议，且域名必须是后台配置的合法域名 |
| data | Object | 否 | 请求的数据 |
| header | Object | 否 | HTTP Header , header 中不能设置 Referer |
| method | String | 否 | 默认是GET，有效值为： OPTIONS, GET, HEAD, POST, PUT, DELETE, TRACE, CONNECT |
| success | Function | 否 | 接口调用成功的回调函数 |
| fail | Function | 否 | 接口调用失败的回调函数 |
| complete | Function | 否 | 接口调用结束的回调函数（调用成功、失败都会执行）|

示例代码：
```js
wx.connectSocket({
  url: 'test.php',
  data:{
    x: '',
    y: ''
  },
  header:{ 
    'content-type': 'application/json'
  },
  method:"GET"
})
```

####wx.onSocketOpen
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

####wx.onSocketError
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

####wx.sendSocketMessage
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


####wx.onSocketMessage
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


####wx.closeSocket
wx.closeSocket()
关闭WebSocket连接。


#wx.onSocketClose
wx.onSocketClose(CALLBACK)
监听WebSocket关闭。
示例代码：
```js
wx.connectSocket({
  url: 'test.php'
})

//注意这里有时序问题，
//如果 wx.connectSocket 还没回调 wx.onSocketOpen，而先调用 wx.closeSocket，那么就做不到关闭 WebSocket 的目的。
//必须在 WebSocket 打开期间调用 wx.closeSocket 才能关闭。
wx.onSocketOpen(function() {
  wx.closeSocket()
})

wx.onSocketClose(function(res) {
  console.log('WebSocket 已关闭！')
})
```


