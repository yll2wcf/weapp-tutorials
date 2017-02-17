# 7-4-2 audio

audio音频，用来加入一段音频，使页面更加丰富。  
audio 所包含的属性：

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
|  |  |  |  |
|  |  |  |  |



