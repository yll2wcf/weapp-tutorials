# 案例

### 仿百思APP

![](/assets/20170207161237.png)

#####项目结构

![](/assets/20170207161913.png)

app.json

```
{
  "pages":[
    "pages/index/index",
    "pages/index/detail",
    "pages/logs/logs",
    "pages/news/news",
    "pages/attention/attention",
    "pages/membercenter/membercenter"
  ],
  "window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "black",
    "navigationBarTitleText": "WeChat",
    "navigationBarTextStyle":"white",
    "backgroundColor": "#eaeaea"
  },
  "tabBar": {
    "color": "black",
    "borderStyle": "white",
    "selectedColor": "rgb(176,170,168)",
    "backgroundColor": "white",
    "list": [{
      "pagePath": "pages/index/index",
      "text": "精华",
      "iconPath": "images/tabBar/tabBar_essence_click_icon.png",
      "selectedIconPath": "images/tabBar/tabBar_essence_icon.png"
    },
    {
      "pagePath": "pages/news/news",
      "text": "最新",
      "iconPath": "images/tabBar/tabBar_new_click_icon.png",
      "selectedIconPath": "images/tabBar/tabBar_new_icon.png"
    },
    {
      "pagePath":"pages/attention/attention",
      "text":"关注",
      "iconPath": "images/tabBar/tabBar_friendTrends_click_icon.png",
      "selectedIconPath": "images/tabBar/tabBar_friendTrends_icon.png"
    },
    {
      "pagePath": "pages/membercenter/membercenter",
      "text": "我",
      "iconPath": "images/tabBar/tabBar_me_click_icon.png",
      "selectedIconPath": "images/tabBar/tabBar_essence_icon.png"
    }]
  },
  "networkTimeout": {
    "request": 10000
  },
  "debug":true
}
```

page:注册页面
window:最上边标题栏样式
tabbar:底部导航栏

页面类型主要是列表，需要创建每个item样式

```
<template name="mainTabCell">
  <view class="top">
    <image class="avator" src="{{item.profile_image}}" mode="aspectFill"></image>
    <view class="title-time">
      <text class="title">{{item.name}}</text>
      <text class="time">{{item.create_time}}</text>
    </view>
    <image class="morebtnnormal" src="../../images/index/morebtnnormal.png" mode="center"></image>
  </view>
  <view class="content">
    <text class="content-text">{{item.text}}</text>
    <view class="content-multimedia" hidden="{{(item.image1 && (!item.videouri && !item.voiceuri))? false:true}}">
      <image hidden="{{true}}" src="{{item.image1}}" mode="scaleToFill" style="width:{{item.width}}rpx;height:{{item.height}}rpx;"></image>
    </view>
    <view class="content-multimedia" hidden="{{item.videouri?false:true}}">
      <video id="{{item.id}}" src="{{item.videouri}}" bindplay="videoPlay" bindeneded="videoEndPlay" controls style="width:{{item.width}}rpx;height:{{item.height}}rpx;"></video>
    </view>
    <view class="content-multimedia" hidden="{{item.voiceuri?false:true}}">
      <audio id="{{item.id}}" src="{{item.voiceuri}}" poster="{{item.bimageuri}}" author="{{item.screen_name}}" bindplay="audioplay" bindeneded="audioEndPlay" controls></audio>
    </view>
  </view>
  <view class="bottom">
    <view class="bottom-item">
      <view class="bottom-item-content">
        <image src="../../images/index/mainCellDing.png" mode="center"></image>
        <text class="bottom-item-zan-text">{{item.love}}</text>
      </view>
      <view class="cut-line"></view>
    </view>
    <view class="bottom-item">
      <view class="bottom-item-content cai">
        <image src="../../images/index/mainCellCai.png" mode="center"></image>
        <text class="bottom-item-zan-text">{{item.hate}}</text>
      </view>
      <view class="cut-line"></view>
    </view>
    <view class="bottom-item">
      <view class="bottom-item-content">
      <image src="../../images/index/mainCellComment.png" mode="center"></image>
      <text class="bottom-item-zan-text">{{item.comment}}</text>
      </view>
    </view>
  </view>
</template>
```

中间内容部分根据返回值是否含有videouri/voiceuri来改变hidden属性

主页面使用swiper实现顶部导航

每个swiper-item加载item模板

```
<swiper-item>
    <scroll-view class="scrollview" scroll-y="true" bindscrolltolower="loadMoreData" bindscrolltoupper="refreshData" scroll-top="{{scrollTop.scroll_top}}" bindscroll="scrollTopFun">
      <view style="height:12rpx;background-color:#eaeaea"></view>
      <view class="item-view" wx:for="{{allDataList}}" wx:for-item="item">
        <navigator url="detail?id={{item.id}}">
          <template is="mainTabCell" data="{{item}}" />
        </navigator>
      </view>
      <view style="height:12rpx;background-color:#eaeaea"></view>
    </scroll-view>
  </swiper-item>
```

添加向上图片用来快速返回顶部

```
<image src="../../images/index/uparrow.png" style="position: absolute; bottom: 50rpx; right: 30rpx; width: 120rpx; height: 120rpx; border-radius:50%; overflow:hidden;" wx:if="{{scrollTop.goTop_show}}" catchtap="goTopFun">
</image>
```

向下滑动切超过100高度才显示向上图片

```
scrollTopFun:function(e){
    if(e.detail.scrollTop<100){
      this.setData({
        'scrollTop.goTop_show':false,
        'scrollTop.top_position':e.detail.scrollTop
      })
    }else if(e.detail.scrollTop<this.data.scrollTop.top_position){
      this.setData({
        'scrollTop.goTop_show':true,
        'scrollTop.top_position':e.detail.scrollTop
      });
    }else{
      this.setData({
        'scrollTop.goTop_show':false,
        'scrollTop.top_position':e.detail.scrollTop
      });
    }
  },
  goTopFun:function(e){
    var _top=this.data.scrollTop.scroll_top;
    if(_top==1){
      _top=0;
    }else{
      _top=1;
    }
    this.setData({
      'scrollTop.scroll_top':_top
    });
  },
```
根据顶部导航栏选择加载数据

```
  setNewDataWithRes: function (res, target) {
    switch (types[dataType]) {
      case DATATYPE.ALLDATATYPE:
        allMaxtime = res.data.info.maxtime;
        target.setData({
          allDataList: res.data.list
        });
        break;
      case DATATYPE.VIDEODATATYPE:
        videoMaxtime = res.data.info.maxtime;
        target.setData({
          videoDataList: res.data.list
        });
        break;
      case DATATYPE.PICTUREDATATYPE:
        pictureMaxtime = res.data.info.maxtime;
        target.setData({
          pictureDataList: res.data.list
        });
        break;
      case DATATYPE.TEXTDATATYPE:
        textMaxtime = res.data.info.maxtime;
        target.setData({
          textDataList: res.data.list
        });
        break;
      case DATATYPE.VOICEDATATYPE:
        voiceMaxtime = res.data.info.maxtime;
        target.setData({
          voiceDataList: res.data.list
        });
        break;
      default:
        break;
    }
  },
  ```

