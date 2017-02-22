###arguments参数

JavaScript还有一个免费赠送的关键字`arguments`，它只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数。arguments类似数组但它不是一个数组：
```js
//index.js
Page({
  onLoad: function () {
    foo("haha", "hehe", "heihei");
  }
})

function foo(x) {
    for (var i=0; i<arguments.length; i++) {
        //依次输出// haha, hehe, heihei        
        console.log(arguments[i]);
    }
}
```

利用arguments，你可以获得调用者传入的所有参数。也就是说，即使函数不定义任何形式参数，还是可以拿到参数的值：
```
function abs() {
    if (arguments.length === 0) {
        return 0;
    }
    var x = arguments[0];
    return x >= 0 ? x : -x;
}
abs(); // 0
abs(10); // 10
abs(-9); // 9
```

实际上`arguments`最常用于判断传入参数的个数。你可能会看到这样的写法：
```
// foo(a[, b], c)
// 接收2~3个参数，b是可选参数，如果只传2个参数，b默认为null：
function foo(a, b, c) {
    if (arguments.length === 2) {
        // 实际拿到的参数是a和b，c为undefined
        c = b; // 把b赋给c
        b = null; // b变为默认值
    }
    // ...
}
```
要把中间的参数`b`变为“可选”参数，就只能通过`arguments`判断，然后重新调整参数并赋值。