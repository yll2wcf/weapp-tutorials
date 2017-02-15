### 对象
JavaScript的对象是一组由键-值组成的无序集合，一般由花括号`{}`包裹例如：
```
var person = {
    name: 'Bob',
    age: 20,
    tags: ['js', 'web', 'mobile'],
    city: 'Beijing',
    hasCar: true,
    zipcode: null
};
```
JavaScript对象的键都是字符串类型，值可以是任意数据类型。上述person对象一共定义了6个键值对，其中每个键又称为对象的属性，例如，person的name属性为'Bob'，zipcode属性为null。

要获取一个对象的属性，我们用对象变量.属性名的方式：
```
person.name; // 'Bob'
person.zipcode; // null
```
细心的同学可能会发现,在小程序的app.js文件中，app()方法里面参数就是一个`{}`包裹的对象。 每个页面的js文件 page()方法里面也是一个对象。