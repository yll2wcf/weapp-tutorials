##7.4.2 audio

audio 音频，用来加入一段音频，使页面更加丰富。  
audio 所包含的属性，如表7-27所示：

表7-27

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| id | String |  | video 组件的唯一标识符 |
| src | String |  | 要播放音频的资源地址 |
| loop | Boolean | false | 是否循环播放 |
| controls | Boolean | true | 是否显示默认控件 |
| poster | String |  | 默认控件上的音频封面的图片资源地址，如果 controls 属性值为 false 则设置 poster 无效 |
| name | String | 未知音频 | 默认控件上的音频名字，如果 controls 属性值为 false 则设置 name 无效 |
| author | String | 未知作者 | 默认控件上的作者名字，如果 controls 属性值为 false 则设置 author 无效 |
| binderror | EventHandle |  | 当发生错误时触发 error 事件，detail = {errMsg: MediaError.code} |
| bindplay | EventHandle |  | 当开始/继续播放时触发play事件 |
| bindpause | EventHandle |  | 当暂停播放时触发 pause 事件 |
| bindtimeupdate | EventHandle |  | 当播放进度改变时触发 timeupdate 事件，detail = {currentTime, duration} |
| bindended | EventHandle |  | 当播放到末尾时触发 ended 事件 |

MediaError.code 错误码，如表7-28所示

表7-28

| 错误码 | 说明 |
| :--- | :--- |
| MEDIA_ERR_ABORTED | 获取资源被用户禁止 |
| MEDIA_ERR_NETWORD | 网络错误 |
| MEDIA_ERR_DECODE | 解码错误 |
| MEDIA_ERR_SRC_NOT_SUPPOERTED | 不合适资源 |

示例代码：
wxml中：
```xml
<view class="audio-view">
  <audio poster="{{poster}}" name="{{name}}" author="{{author}}" src="{{src}}" id="myAudio" controls loop></audio>
</view>
<view class="audio-view">
  <button class="button" type="default" bindtap="audioPlay">播放</button>
  <button class="button" type="default" bindtap="audioPause">暂停</button>
  <button class="button" type="default" bindtap="audio14">设置当前播放时间为14秒</button>
  <button class="button" type="default" bindtap="audioStart">回到开头</button>
</view>
```
js中：
```js
Page({
  data:{
    poster: '音频封面地址',
    name: '音频名称',
    author: '音频作者',
    src: '音频资源地址',
  },
  audioPlay: function () {
    this.audioCtx.play()
  },
  audioPause: function () {
    this.audioCtx.pause()
  },
  audio14: function () {
    this.audioCtx.seek(14)
  },
  audioStart: function () {
    this.audioCtx.seek(0)
  },
  onLoad:function(options){
    // 页面初始化 options为页面跳转所带来的参数
  },
  onReady:function(){
    // 页面渲染完成
    // 使用 wx.createAudioContext 获取 audio 上下文 context
    this.audioCtx = wx.createAudioContext('myAudio')
  },
  onShow:function(){
    // 页面显示
  },
  onHide:function(){
    // 页面隐藏
  },
  onUnload:function(){
    // 页面关闭
  }
})
```
运行效果如图7-18所示：


![](/assets/图7-18 audio组件示例运行效果图.png)


图7-18 audio组件示例运行效果图






