###定义函数
在JavaScript中，定义函数用`function`关键字，主要方式如下：
```
function abs(x) {
    if (x >= 0) {
        return x;
    } else {
        return -x;
    }
}
```
上述abs()函数的定义如下：

+ function指出这是一个函数定义；
+ abs是函数的名称；
+ (x)括号内列出函数的参数，多个参数以,分隔；
+ { ... }之间的代码是函数体，可以包含若干语句，甚至可以没有任何语句。