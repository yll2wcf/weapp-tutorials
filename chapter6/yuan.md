### 子元素属性

子元素属性定义了伸缩项目的属性。

![](/assets/6-7.png) 图6-7

##### order

子元素默认按照编写的顺序排列，使用order属性可以更改这一方式，使所有子元素按order从小到大排列,这个值可以为负数。

```
.view{
	order: 1;
}
```

##### flex-grow

此属性定义了子元素的扩展能力，数值越大在布局中占得比例越大，且大小与这个数值成正比。负值无效。

```
.view{
	flex-grow: 2;
}
```

例如图6-8所示：

![](/assets/6-8.png)图6-8

##### flex-shrink

与flex-grow相对，定义了子元素收缩的能力。负值无效。

```
.view{
	flex-shrink: 2;
}
```

##### flex-basis

定于伸缩的基准值，项目会按这个比例进行伸缩。默认值为auto，即根据flex-grow的值进行伸缩。

```
.view{
	flex-basis: 0 | auto ;
}
```
#### flex

前面三种属性的缩写，第二个值（flex-shrink）与第三个值（flex-basis）可以省略，默认值为 0 1 auto。

```
.view{
	flex: 1;
}
```
这里建议使用flex而不是分别设置三个属性，使用flex会智能的设置其他的属性。

###### align-self

用来覆盖父组件样式中的alignItems的值，是子元素拥有自己想要的对齐方式。

```
.view{
	align-self: flex-end;
}
```

例如在父组件alignItems为flex-start时，将子组件align-self设置为flex-end的示意图6-9。

![](/assets/6-9.png) 图6-9