#3.4.3 JSON
JSON是JavaScript Object Notation的缩写，它是一种数据交换格式。我们在进行网络请求传输数据的时候，基本上都用JSON传输了。

JSON实际上是JavaScript的一个子集。在JSON中，一共就这么几种数据类型：

* `number`：和JavaScript的number完全一致；
* `boolean`：就是JavaScript的`true`或`false`；
* `string`：就是JavaScript的`string`；
* `null`：就是JavaScript的`null`；
* `array`：就是JavaScript的Array表示方式——`[]`；
* `object`：就是JavaScript的`{ ... }`表示方式。

以及上面的任意组合。

并且，JSON还定死了字符集必须是UTF-8，表示多语言就没有问题了。为了统一解析，JSON的字符串规定必须用双引号`""`，Object的键也必须用双引号`""`。

任何JavaScript对象变成JSON，就是把这个对象序列化成一个JSON格式的字符串，这样才能够通过网络传递给其他计算机。


为了方法操作JSON格式化数据，JavaScript提供了`JSON`对象,主要两个方法:

1. `stringify()` 把JavaScript对象转换成JSON格式的字符串。
2. `parse()` 把JSON格式的字符串转换成JavaScript对象

```
var zhangsan = {
    name: '张三',
    age: 18
};
JSON.stringify(xiaoming); //// {"name":"张三","age":18}
```

```
//输出 // Object {name: '张三', age: 18}
JSON.parse('{"name":"张三","age":18}'); 
```