#wx.connectSocket
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


