##7.4.1 image

image 图片，用于界面显示图片，是程序中比较常见的组件。它的默认宽度300px、高度225px。  
image 所包含的属性，如表7-24所示：

表7-24

| 属性名 | 类型 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- |
| src | String |  | 图片资源地址 |
| mode | String | 'scaleToFill' | 图片裁剪、缩放的模式 |
| binderror | HandleEvent |  | 当错误发生时，发布到 AppService 的事件名，事件对象event.detail = {errMsg: 'something wrong'} |
| bindload | HandleEvent |  | 当图片载入完毕时，发布到 AppService 的事件名，事件对象event.detail = {height:'图片高度px', width:'图片宽度px'} |

其中，mode 有 13 种模式，其中 4 种是缩放模式，9 种是裁剪模式。

缩放模式，如表7-25所示：

表7-25

| 模式 | 说明 |
| :--- | :--- |
| scaleToFill | 不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素 |
| aspectFit | 保持纵横比缩放图片，使图片的长边能完全显示出来。也就是说，可以完整地将图片显示出来。 |
| aspectFill | 保持纵横比缩放图片，只保证图片的短边能完全显示出来。也就是说，图片通常只在水平或垂直方向是完整的，另一个方向将会发生截取。 |
| widthFix | 宽度不变，高度自动变化，保持原图宽高比不变 |

裁剪模式，如表7-26所示：

表7-26

| 模式 | 说明 |
| :--- | :--- |
| top | 不缩放图片，只显示图片的顶部区域 |
| bottom | 不缩放图片，只显示图片的底部区域 |
| center | 不缩放图片，只显示图片的中间区域 |
| left | 不缩放图片，只显示图片的左边区域 |
| right | 不缩放图片，只显示图片的右边区域 |
| top left | 不缩放图片，只显示图片的左上边区域 |
| top right | 不缩放图片，只显示图片的右上边区域 |
| bottom left | 不缩放图片，只显示图片的左下边区域 |
| bottom right | 不缩放图片，只显示图片的右下边区域 |

示例代码：
wxml中：
```xml
<view wx:for="{{array}}" wx:for-item="item">
  <view>{{item.text}}</view>
  <view class="image">
    <image style="width: 200px; height: 200px; background-color: #eeeeee;" mode="{{item.mode}}" src="{{src}}"></image>
  </view>
</view>
```
js中：
```js
Page({
  data:{
    array: [{
      mode: 'aspectFit',
      text: 'aspectFit：保持纵横比缩放图片，使图片完整的显示出来'
    }, { 
      mode: 'scaleToFill',
      text: 'scaleToFill：不保持纵横比缩放图片，使图片拉伸适应'
    }, { 
      mode: 'aspectFill',
      text: 'aspectFill：保持纵横比缩放图片，只保证图片的短边能完全显示出来'
    }, { 
      mode: 'top',
      text: 'top：不缩放图片，只显示图片的顶部区域' 
    }, {      
      mode: 'bottom',
      text: 'bottom：不缩放图片，只显示图片的底部区域'
    }, { 
      mode: 'center',
      text: 'center：不缩放图片，只显示图片的中间区域'
    }, { 
      mode: 'left',
      text: 'left：不缩放图片，只显示图片的左边区域'
    }, { 
      mode: 'right',
      text: 'right：不缩放图片，只显示图片的右边区域'
    }, { 
      mode: 'top left',
      text: 'top left：不缩放图片，只显示图片的左上边区域' 
    }, { 
      mode: 'top right',
      text: 'top right：不缩放图片，只显示图片的右上边区域'
    }, { 
      mode: 'bottom left',
      text: 'bottom left：不缩放图片，只显示图片的左下边区域'
    }, { 
      mode: 'bottom right',
      text: 'bottom right：不缩放图片，只显示图片的右下边区域'
    }],
    src: '../resources/testImage.png'
  },
  imageError: function(e) {
    console.log('image3发生error事件，携带值为', e.detail.errMsg)
  },

})
```
运行效果如图7-17所示：

![](/assets/图7-17 image组件示例运行效果图.png)

图7-17 image组件示例运行效果图


