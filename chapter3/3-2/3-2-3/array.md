###数组
>数组,英文为Array 

数组是一组按顺序排列的集合，集合的每个值称为元素。不同于Java等编程语言,JavaScript的数组可以包括任意数据类型。例如：
```
[1, 3.14, 'Hello', null, true];
```
上述数组包含5个元素。数组用[]表示，元素之间用,分隔。

另一种创建数组的方法是通过Array()函数实现：
```
new Array(1, 2, 3); // 创建了数组[1, 2, 3]
```
然而，出于代码的可读性考虑，强烈建议直接使用[]。
数组的元素可以通过索引来访问。请注意，索引的起始值为0：
```
var arr = [1,3.14, 'Hello', null, true];
arr[0]; // 返回索引为0的元素，即1
arr[4]; // 返回索引为4的元素，即true
arr[5]; // 索引超出了范围，返回undefined
```

要取得Array的长度，直接访问length属性：
```
var arr = [1,3.14, 'Hello', null, true];
console.log(arr.length); //输出5
```

**请注意，直接给Array的length赋一个新的值会导致Array大小的变化**：

```
var arr = [1, 2, 3];
arr.length; // 3
arr.length = 6; //长度变成6
arr; // arr变为[1, 2, 3, undefined, undefined, undefined]
arr.length = 2;
arr; // arr变为[1, 2]
```

`Array`可以通过索引把对应的元素修改为新的值，因此，对Array的索引进行赋值会直接修改这个Array：
```
var arr = ['A', 'B', 'C'];
arr[1] = 520;
arr; // arr现在变为['A', 520, 'C']
```