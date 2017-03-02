### 布尔值

一个布尔值只有true、false两种值，要么是true，要么是false，可以直接用true、false表示布尔值，也可以通过布尔运算计算出来：

```js
true; // 这是一个true值
false; // 这是一个false值
2 > 1; // 这是一个true值
2 >= 3; // 这是一个false值
```
在条件语句中,我们还可以用非0表示true, 0表示false
```js      
if(1){  //改成0不会输出
  console.log("非0表示true");
}
```

除了0,JavaScript把`null`、`undefined`、`NaN`和空字符串`''`都视为`false`，其他值一概视为`true`。