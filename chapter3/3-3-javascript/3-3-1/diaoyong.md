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

由于JavaScript允许传入任意个参数而不影响调用，因此传入的参数比定义的参数多也没有问题，虽然函数内部并不需要这些参数：
```
abs(-9, 'haha'); // 返回9
abs(10, 'hehe', null); // 返回10
```
传入的参数比定义的少也没有问题：
```console.log(abs()); //输出NaN```

此时abs(x)函数的参数x将收到undefined，计算结果为NaN。

要避免收到undefined，可以对参数进行检查：
```
function abs(x) {
    if (typeof x !== 'number') {
        throw 'Not a number';
    }
    if (x >= 0) {
        return x;
    } else {
        return -x;
    }
}
```