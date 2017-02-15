# 7-3-4 input

input输入框，类似于一个文本编辑器，用来和用户进行文本交互。  
input所包含的属性：

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| value | String |  | 输入框的初始内容 |
| type | String | text | input 的类型，有效值：text, number, idcard, digit |
| password | Boolean | false | 是否是密码类型 |
| placeholder | String |  | 输入框为空时占位符 |
| placeholder-style | String |  | 指定 placeholder 的样式 |
| placeholder-class | String | input-placeholder | 指定 placeholder 的样式类 |
| disabled | Boolean | false | 是否禁用 |
| maxlength | Number | 140 | 最大输入长度，设置为 -1 的时候不限制最大长度 |
| cursor-spacing | Number | 0 | 指定光标与键盘的距离，单位 px 。取 input 距离底部的距离和 cursor-spacing 指定的距离的最小值作为光标与键盘的距离 |
| auto-focus | Boolean | false | \(即将废弃，请直接使用 focus \)自动聚焦，拉起键盘 |
| focus | Boolean | false | 获取焦点 |
| bindinput | EventHandle |  | 当键盘输入时，触发input事件，event.detail = {value: value}，处理函数可以直接 return 一个字符串，将替换输入框的内容。 |
| bindfocus | EventHandle |  | 输入框聚焦时触发，event.detail = {value: value} |
| bindblur | EventHandle |  | 输入框失去焦点时触发，event.detail = {value: value} |
| bindconfirm | EventHandle |  | 点击完成按钮时触发，event.detail = {value: value} |



