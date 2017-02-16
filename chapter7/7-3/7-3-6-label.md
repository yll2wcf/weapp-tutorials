#7-3-7 label
label 用来改进表单组件的可用性，使用 for 属性找到对应的 id，或者将控件放在该标签下，当点击时，就会触发对应的控件。
for 优先级高于内部控件，内部有多个控件的时候默认触发第一个控件。
目前可以绑定的控件有：button, checkbox, radio, switch组件。
label 只包含一个 for 属性：
