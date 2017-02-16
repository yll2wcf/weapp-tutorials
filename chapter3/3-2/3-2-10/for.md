###for循环

我们用`for`循环计算下1+2+3+...+10000，代码如下：
```
var x = 0;
var i;
for (i=1; i<=10000; i++) {
    x = x + i;
}
x; // 50005000
```

让我们来分析一下`for`循环的控制条件：

1. i=1 这是初始条件，将变量i置为1；
2. i<=10000 这是判断条件，满足时就继续循环，不满足就退出循环；
3. i++ 这是每次循环后的递增条件，由于每次循环后变量i都会加1，因此它终将在若干次循环后不满足判断条件i<=10000而退出循环。

for循环最常用的地方是利用索引来遍历数组：

```
var arr = ['Apple', 'Google', 'Microsoft'];
var i, x;
for (i=0; i<arr.length; i++) {
    x = arr[i];
    console.log(x);
}
```
`for`循环的3个条件都是可以省略的，如果没有退出循环的判断条件，就必须使用break语句退出循环，否则就是死循环(不要在开发环境中测试死循环,容易卡住界面)：
```
var x = 0;
for (;;) { // 将无限循环下去
    if (x > 100) {
        break; // 通过if判断来退出循环
    }
    x ++;
}
```

当`for`循环语句内只有一行执行语句可以省略`{}`但是不建议这么写。比如下面有一个凄美的爱情故事:
>一个男孩给女孩写了一行代码 
```
for(;;) console.log("I love You!");
```
女孩回了一行代码
```
for(;;); console.log("I love You Too!");
```
很凄美。

代码解释下, 女孩代码`for` 循环后多了一个`;` 输出语句属于for循环之外的语句,后面的内容永远执行不到。

####for ... in

`for`循环的一个变体是`for ... in`循环，它可以把一个对象的所有属性依次循环出来：
```
var o = {
    name: 'Jack',
    age: 20,
    city: 'Beijing'
};
for (var key in o) {
    console.log(key); // 'name', 'age', 'city'
    console.log(o[key]); // 'Jack' ,20 ,'Beijing'  
}
```
由于数组也是特殊的对象，而它的每个元素的索引被视为对象的属性，因此，`for ... in`循环可以直接循环出数组的索引：
```
var a = ['A', 'B', 'C'];
for (var i in a) {
    console.log(i); // '0', '1', '2'
    console.log(a[i]); // 'A', 'B', 'C'
}
```