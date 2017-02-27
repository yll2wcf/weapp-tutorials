# 7-4-3 video

video视频，用来加入视频播放功能，使页面更加丰富。video标签认宽度300px、高度225px，设置宽高需要通过wxss设置width和height。  
video所包含的属性，如表7-29所示：

表7-29

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| src | String |  | 要播放视频的资源地址 |
| controls | Boolean | true | 是否显示默认播放控件（播放/暂停按钮、播放进度、时间） |
| danmu-list | Object Array |  | 弹幕列表 |
| danmu-btn | Boolean | false | 是否显示弹幕按钮，只在初始化时有效，不能动态变更 |
| enable-danmu | Boolean | false | 是否展示弹幕，只在初始化时有效，不能动态变更 |
| autoplay | Boolean | false | 是否自动播放 |
| bindplay | EventHandle |  | 当开始/继续播放时触发play事件 |
| bindpause | EventHandle |  | 当暂停播放时触发 pause 事件 |
| bindended | EventHandle |  | 当播放到末尾时触发 ended 事件 |
| bindtimeupdate | EventHandle |  | 播放进度变化时触发，event.detail = {currentTime: '当前播放时间'} 。触发频率应该在 250ms 一次 |
| objectFit | String | contain | 当视频大小与 video 容器大小不一致时，视频的表现形式。contain：包含，fill：填充，cover：覆盖 |

示例代码：
wxml中：
```xml
<view class="video-view">
  <video id="myVideo" src="视频资源地址"
  danmu-list="{{danmuList}}" enable-danmu danmu-btn controls></video>
</view>
<view class="view">
  <button bindtap="bindButtonTap">获取视频</button>
  <view class="view">
    <view class="weui-cell__hd">
      <view class="weui-label">弹幕内容</view>
    </view>
    <view class="weui-cell__bd">
      <input bindblur="bindInputBlur" class="input-view" type="text" placeholder="在此处输入弹幕内容" />
    </view>
  </view>
  <button class="view" type="primary" bindtap="bindSendDanmu">发送弹幕</button>
</view>
```
js中：
```js
function getRandomColor() {
  let rgb = []
  for (let i = 0; i < 3; ++i) {
    let color = Math.floor(Math.random() * 256).toString(16)
    color = color.length == 1 ? '0' + color : color
    rgb.push(color)
  }
  return '#' + rgb.join('')
}
Page({
  inputValue: '',
  data: {
    src: '',
    danmuList: [
      {
        text: '第 1s 出现的弹幕',
        color: '#ff0000',
        time: 1
      },
      {
        text: '第 3s 出现的弹幕',
        color: '#ff00ff',
        time: 3
      }]
  },
  bindButtonTap: function () {
    var that = this
    wx.chooseVideo({
      sourceType: ['album', 'camera'],
      maxDuration: 60,
      camera: ['front', 'back'],
      success: function (res) {
        that.setData({
          src: res.tempFilePath
        })
      }
    })
  },
  bindSendDanmu: function () {
    this.videoContext.sendDanmu({
      text: this.inputValue,
      color: getRandomColor()
    })
  },
  onLoad: function (options) {
    // 页面初始化 options为页面跳转所带来的参数
  },
  onReady: function (res) {
    // 页面渲染完成
    this.videoContext = wx.createVideoContext('myVideo')
  },
  onShow: function () {
    // 页面显示
  },
  onHide: function () {
    // 页面隐藏
  },
  onUnload: function () {
    // 页面关闭
  }
})
```
运行效果如题7-19所示：

![](/assets/图7-19 video组件示例运行效果图.png)


