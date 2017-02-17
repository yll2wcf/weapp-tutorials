# 7-4-3 video

video视频，用来加入视频播放功能，使页面更加丰富。  
video所包含的属性：

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



