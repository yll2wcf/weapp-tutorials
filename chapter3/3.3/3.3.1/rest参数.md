###rest参数
ES6标准引入了`rest`参数，多余的参数以数组形式交给变量`rest`，所以，不再需要`arguments`我们就获取了全部参数。

`rest`参数只能写在最后，前面用`...`标识，如果传入的参数连正常定义的参数都没填满也不要紧，`rest`参数会接收一个空数组（注意不是`undefined`）。

示例代码:
```js
//index.js
Page({
  onLoad: function () {
    foo("haha", "hehe", "heihei");
  }
})

function foo(x, ...rest) {
    console.log(x); //输出haha
    console.log(rest);//输出["hehe", "heihei"]
}

```