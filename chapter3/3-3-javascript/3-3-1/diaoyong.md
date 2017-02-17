###调用函数
调用函数时，按顺序传入参数即可，修改index.js，如下
```
//index.js
Page({

  onLoad: function () {
    console.log(abs(-9)); //输出9
    console.log(abs(10)); //输出10
  }
})
//定义函数
var abs = function (x) {
    if (x >= 0) {
        return x;
    } else {
        return -x;
    }
};
```