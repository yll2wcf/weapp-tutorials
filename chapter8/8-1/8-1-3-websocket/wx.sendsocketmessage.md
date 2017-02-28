#wx.sendSocketMessage
wx.sendSocketMessage(OBJECT)
通过 WebSocket 连接发送数据，需要先 wx.connectSocket，并在 wx.onSocketOpen 回调之后才能发送。
OBJECT参数说明：