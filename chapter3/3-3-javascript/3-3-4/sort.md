###sort函数

介绍数组的时候讲过`sort()` 函数，其实`sort()`函数也是一个高阶函数，接收一个函数作为参数,函数的作用就是指定排序规则。
比如按照数字大小排序,我们可以这么写:
```
var arr = [10, 20, 1, 2];
arr.sort(function (x, y) {
    if (x < y) {
        return -1;
    }
    if (x > y) {
        return 1;
    }
    return 0;
}); // [1, 2, 10, 20]
```