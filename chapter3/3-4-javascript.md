#4.JavaScript标准对象

在JavaScript语言中，你可以认为一切都是对象，我们通常用`typeof`操作符获取对象的类型，它总是返回一个字符串：
```js
typeof 123; // 'number'
typeof NaN; // 'number'
typeof 'str'; // 'string'
typeof true; // 'boolean'
typeof undefined; // 'undefined'
typeof Math.abs; // 'function'
typeof null; // 'object'
typeof []; // 'object'
typeof {}; // 'object'
```
可见，`number`、`string`、`boolean`、`function`和`undefined`有别于其他类型。特别注意`null`的类型是`object`，`Array`的类型也是`object`，如果我们用`typeof`将无法区分出`null`、`Array`和通常意义上的`object`——`{}`。

JavaScript本身还提供了常用的对象，方便我们开发:

1. Date
2. RegExp
3. JSOn
4. Math