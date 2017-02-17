#3.4.1 Date
Date 对象用于处理日期和时间。
创建 Date 对象的语法：
```
var myDate=new Date()
```
如果要创建一个指定日期和时间的Date对象，可以用：
```
// 传入2017年 1月 9号 8点 15分 30秒 100毫秒
var d = new Date(2017, 0, 9, 8, 15, 30,100);
console.log(d);//输出 Mon Jan 09 2017 08:15:30 GMT+0800 (CST)
```