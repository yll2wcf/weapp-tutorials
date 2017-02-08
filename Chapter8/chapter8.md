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
  
  每个item添加跳转到评论页的navigator并传入id
  ```
  <navigator url="detail?id={{item.id}}">
  ```
  评论页与主页面类似,commentCell为item的模板,detail页面里使用这个模板,实现下拉加载更多功能
  
  ```
  onReachBottom: function () {
        util.showLoading();
        var that = this;
        var parameters = "a=dataList&c=comment&data_id=" + data_id + "&page=" + (page + 1) + "&lastcid=" + lastcid;
        util.request(parameters, function (res) {
            if (res.data.data) {
                page += 1;
                that.setData({
                    dataList: that.data.dataList.concat(res.data.data)
                });
                lastcid = res.data.data[res.data.data.length - 1].id;
                setTimeout(function () {
                    util.hideToast();
                    wx.stopPullDownRefresh();
                }, 1000);
            } else {
                util.showSuccess("NO MORE...", 300);
            }
        });
    }
    ```
  
  
### 仿QQ音乐

项目结构

![](/assets/20170208155947.png)

resources为项目所用图片资源,services是网络请求,utils工具类

例如search.js为搜索用请求

```
(function (exports) {

    exports.getHotSearchKeys = function (callback) {
        var data = {
            g_tk: 5381,
            uin: 0,
            format: 'json',
            inCharset: 'utf-8',
            outCharset: 'utf-8',
            notice: 0,
            platform: 'h5',
            needNewCode: 1,
            _: Date.now()
        };
        wx.request({
            url: 'http://c.y.qq.com/splcloud/fcgi-bin/gethotkey.fcg',
            data: data,
            header: {
                'Content-Type': 'application/json'
            },
            success: function (res) {
                if (res.statusCode == 200) {
                    callback(res.data)
                } else {

                }
            }
        });
    };

}(module.exports));
```
这种写法与先定义function，最后用module.exports输出一样

程序主页

![](/assets/20170208160610.png)![](/assets/20170208171808.png)![](/assets/20170208171826.png)

推荐页面

```
<view hidden="{{mainView != 1}}">
  <swiper indicator-dots="{{indicatorDots}}" autoplay="{{autoplay}}" interval="{{interval}}" duration="{{duration}}">
    <block wx:for="{{slider}}"  wx:key="unique">
      <swiper-item data-id="{{item.id}}" data-url="{{item.linkUrl}}">
        <image src="{{item.picUrl}}" style="height:100%" class="slide-image"/>
      </swiper-item>
    </block>
  </swiper>
  <view class="channel">
    <text class="channel-title">电台</text>
    <view class="radio-list" >
      <block wx:for="{{radioList}}"  wx:key="unique">
        <view class="radio-item" data-id="{{item.radioid}}" data-ftitle="{{item.Ftitle}}" bindtap="radioTap">
          <image class="radio-img" mode="aspectFit" style="height:167.5px;" src="{{item.picUrl}}"/>
          <text class="radio-text">{{item.Ftitle}}</text>
        </view>
      </block>
    </view>
  </view>
  <view class="channel">
    <text class="channel-title">热门歌曲</text>
    <view class="radio-list">
      <view class="radio-item" wx:for="{{songList}}"  wx:key="unique" data-id="{{item.id}}" data-imgsrc="{{item.picUrl}}" bindtap="hotMusicTap">
        <image class="radio-img" mode="aspectFit" style="height:167.5px;" src="{{item.picUrl}}"/>
        <text class="radio-text">{{item.songListDesc}}</text>
      </view>
    </view>
  </view>
</view>
```
这里依靠mainView的值切换页面,点击上方标签会更改mainView的值

