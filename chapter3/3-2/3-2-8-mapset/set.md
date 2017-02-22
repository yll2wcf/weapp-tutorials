###Set
`Set`和`Map`类似，也是一组key的集合，但不存储value。由于`key`不能重复，所以，在Set中，没有重复的key。可以把Set简单理解为没有重复元素的数组。

要创建一个`Set`，需要提供一个数组作为输入，或者直接创建一个空`Set`：

```js
var s1 = new Set(); // 空Set
var s2 = new Set([1, 2, 3]); // 含1, 2, 3
```
重复元素在Set中自动被过滤：
```
var s = new Set([1, 2, 3, 3, '3']);
s; // Set {1, 2, 3, "3"}
```
注意数字`3`和字符串`'3'`是不同的元素。

通过`add(key)`方法可以添加元素到Set中，可以重复添加，但不会有效果，通过delete(key)方法可以删除元素。

```
var s=new Set();
s.add(1);
s.add(1);
console.log(s); //输出 Set {1}
s.delete(1);
console.log(s); //输出 Set {}
s.delete(2);  //没有相应的key也不会报错
```