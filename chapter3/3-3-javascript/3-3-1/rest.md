###rest参数
ES6标准引入了rest参数，多余的参数以数组形式交给变量rest，所以，不再需要arguments我们就获取了全部参数。

rest参数只能写在最后，前面用`...`标识,如果传入的参数连正常定义的参数都没填满，也不要紧，rest参数会接收一个空数组（注意不是`undefined`）。

示例代码:
```
//index.js
Page({
  onLoad: function () {
    foo("haha", "hehe", "heihei");
  }
})

function foo(x, ...rest) {
    console.log(x);
    console.log(rest);
}

```