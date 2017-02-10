####首页index


开始构建小程序首页。


第一步，我们需要创建顶部的导航栏，效果应该类似图10-2：


![](/assets/20170210170336.png) 图10-2


可以看到这个导航栏由三个按键组成，三个按键平分屏幕宽度，文字居中显示，在选中后下方有绿色边框。

为了实现这一效果，这里采取一个比较简单的做法，为每个标签的每个状态（选中/未选中）创建一个view。

```
<view class="tab">
  <view class="tab-item tab-item-active" bindtap="tabItemTap" data-view="1" wx:if="{{mainView==1}}">推荐</view>
  <view class="tab-item" data-view="1" bindtap="tabItemTap" wx:if="{{mainView!=1}}">推荐</view>
  <view class="tab-item tab-item-active" bindtap="tabItemTap" data-view="2" wx:if="{{mainView==2}}">排行榜</view>
  <view class="tab-item" data-view="2" bindtap="tabItemTap" wx:if="{{mainView!=2}}">排行榜</view>
  <view class="tab-item tab-item-active" bindtap="tabItemTap" data-view="3" wx:if="{{mainView==3}}">搜索</view>
  <view class="tab-item" data-view="3" bindtap="tabItemTap" wx:if="{{mainView!=3}}">搜索</view>
</view>
```
```
.tab-item {
  float: left;
  width: 33.333333%;
  height: 43px;
  font-size: 16px;
  text-align: center;
}
.tab-item-active {
  color: #31c27c;
  border-bottom: 2px solid #31c27c;
}
```

所有6个view都享有tab-item这个class的属性，在这里定义了组件的宽度为1/3，字体居中显示以及字号。三个布局拥有tab-item-active属性，这个属性为这个view添加了底部的绿色边框。mainView为控制这一组件的值，当mainView=1时，根据wx：if属性，只有带下边框的“推荐”view与不带下边框的“排行榜”，“搜索”会被渲染，也就实现了我们想要的结果。




