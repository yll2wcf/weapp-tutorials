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

要获取一个对象的属性，我们用对象变量.属性名的方式,访问一个不存在的属性也不会报错，而是返回`undefined`
```
person.name; // 'Bob'
person.zipcode; // null
person.sex; //undefined 
```

细心的同学可能会发现,在小程序的app.js文件中，app()方法里面参数就是一个`{}`包裹的对象。 每个页面的js文件 page()方法里面也是一个对象。


####操作对象

由于JavaScript的对象是动态类型，你可以自由地给一个对象添加或删除属性：
```
var xiaoming = {
    name: '小明'
};
xiaoming.age; // undefined
xiaoming.age = 18; // 新增一个age属性
xiaoming.age; // 18
delete xiaoming.age; // 删除age属性
xiaoming.age; // undefined
delete xiaoming.name; // 删除name属性
xiaoming.name; // undefined
delete xiaoming.school; // 删除一个不存在的school属性也不会报错
```

如果我们要检测xiaoming是否拥有某一属性，可以用in操作符：
```
var xiaoming = {
   name: '小明',
};
console.log('name' in xiaoming);//输出true
```