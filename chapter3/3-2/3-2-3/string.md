###字符串
>字符串英文名称 String

**字符串是以单引号`'`或双引号`"`括起来的任意文本**，比如'abc'，"xyz"等等。
>请注意，`''`或`""`本身只是一种表示方式，不是字符串的一部分，因此，字符串'abc'只有a，b，c这3个字符。

如果单引号`'`本身也是一个字符，那就可以用""括起来，比如:
```js
"I'm OK"
```
包含的字符是`I`，`'`，`m`，`空格`，`O`，`K`这6个字符。

####转义符号

如果字符串内部既包含单引号`'`又包含双引号`"`怎么办？可以用转义字符`\`来标识，比如：
```js
'I\'m \"OK\"!';
```
表示的字符串内容是：`I'm "OK"!`

转义字符`\`可以转义很多字符，比如`\n`表示换行，`\t`表示制表符，字符`\`本身也要转义，所以`\\`表示的字符就是`\`。

ASCII字符可以以\x##形式的十六进制表示，例如：
```
'\x41'; // 完全等同于 'A'
```
还可以用\u####表示一个Unicode字符：
```
'\u4e2d\u6587'; // 完全等同于 '中文'
```
####多行字符串

由于多行字符串用`\n`写起来比较费事，所以最新的ES6标准新增了一种多行字符串的表示方法，用\` ... \`表示,反引号是键盘数字1旁边的按键：
```js
  console.log(`这是
              多行
              字符串`);
```
#### 模板字符串
要把多个字符串连接起来，可以用`+`号连接：
```
var name = '小明';
var age = 20;
var message = '你好, ' + name + ', 你今年' + age + '岁了!';
console.log(message);// 输出 您好小明，你今年20岁了!
```
如果有很多变量需要连接，用`+`号就比较麻烦。ES6新增了一种模板字符串，表示方法和上面的多行字符串一样，但是它会自动替换字符串中的变量：
```
var name = '小明';
var age = 20;
var message = `你好, ${name}, 你今年${age}岁了!`;
console.log(message);// 输出 您好小明，你今年20岁了!
```
#### 操作字符串
字符串常见的操作如下，通过`lengh`可以获取字符串长度。
```
var s = 'Hello, world!';
s.length; // 13
```
要获取字符串某个指定位置的字符，使用下标操作，索引号从0开始,这和我们后面要介绍的数组操作类似：
```
var s = 'Hello, world!';

s[0]; // 'H'
s[6]; // ' '
s[7]; // 'w'
s[12]; // '!'
s[13]; // undefined 超出范围的索引不会报错，但一律返回undefined
```
**需要特别注意的是，字符串是不可变的，如果对字符串的某个索引赋值，在小程序中会报错**
```
var s = 'Test';
s[0] = 'X';  //报错
```

####indexOf()
字符串可以通过调用indexOf()方法找某字符在字符串中的位置。如下:
```      
var str="hello world";
var index=str.indexOf('w');
console.log(index);//输出6 
```
没有找到输出-1。

####substring()
字符串可以通过substring()方法截取字符串的一部分,返回新的字符串。
```
var str="hello world";
var subStr1=str.substr(1);//从索引1开始到结束
console.log(subStr1);  //输出 "ello world"
var subStr2=str.substr(0,3);//从索引0开始，到索引3结束，但不包括索引3
console.log(subStr2); //输出 "hel" 
```

####toUpperCase()

`toUpperCase()`把一个字符串全部变为大写：

```
var s = 'Hello';
s.toUpperCase(); // 返回'HELLO'
```
####toLowerCase()
`toLowerCase()`把一个字符串全部变为小写：
```
var s = 'Hello';
var lower = s.toLowerCase(); // 返回'hello'并赋值给变量lower
lower; // 'hello'
```