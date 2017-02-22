#3.4.1 Date
Date 对象用于处理日期和时间。
创建 Date 对象的语法：
```js
var myDate=new Date()
```
如果要创建一个指定日期和时间的Date对象，可以用：
```js
// 传入2017年 1月 9号 8点 15分 30秒 100毫秒
var d = new Date(2017, 0, 9, 8, 15, 30,100);
console.log(d);//输出 Mon Jan 09 2017 08:15:30 GMT+0800 (CST)
```
可以看到我们传的参数除了月份都比较合理，而月份是从0开始计数，也就是范围是0-11，0表示1月,这点还是非常坑。

除了上面两种,还可以传入距离1970年1月1号0点的毫秒值。
```js
var d = new Date(1483920930100);
console.log(d); //输出Mon Jan 09 2017 08:15:30 GMT+0800 (CST)
```

Date对象方法很多，常用的有下面这些:
```js
var now = new Date();
now.getFullYear(); // 获取年
now.getMonth(); //获取月份,0表示1 范围0-11
now.getDate(); // 获取日期 比如9号
now.getDay(); // 获取星期 如星期三，返回3
now.getHours(); //获取小时数 24小时制
now.getMinutes(); // 获取分钟
now.getSeconds(); // 获取秒
now.getMilliseconds(); // 获取秒
now.getTime(); // 以number形式表示的时间戳如:1483920930100
```