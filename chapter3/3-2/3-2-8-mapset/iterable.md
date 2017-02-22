###iterable

遍历数组可以采用下标循环，遍历`Map`和`Set`就无法使用下标。为了统一集合类型，ES6标准引入了新的`iterable`类型，数组、`Map`和`Set`都属于iterable类型。

具有iterable类型的集合可以通过新的`for ... of`循环来遍历。

for ... of循环是ES6引入的新的语法，

```js
var m = new Map([['小明', 95], ['张三', 75], ['李四', 85]]);
for (var x of m) {
   //依次输出 ["小明", 95] ，["张三", 75] ,["李四", 85]
   console.log(x);  
}
```