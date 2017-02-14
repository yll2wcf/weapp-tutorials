# 3.1 JavaScript简介


>要了解JavaScript，我们首先要回顾一下JavaScript的诞生。

在上个世纪的1995年，当时的网景公司正凭借其Navigator浏览器成为Web时代开启时最著名的第一代互联网公司。

由于网景公司希望能在静态HTML页面上添加一些动态效果，于是叫Brendan Eich这哥们在两周之内设计出了JavaScript语言。你没看错，这哥们只用了10天时间。

为什么起名叫JavaScript？原因是当时Java语言非常红火，所以网景公司希望借Java的名气来推广，但事实上JavaScript除了名字上有点像Java，其他部分基本上没啥关系。JavaScript和Java的关系类似于雷峰塔和雷锋的关系。

> ECMAScript的来历

因为网景开发了JavaScript，一年后微软又模仿JavaScript开发了JScript，为了让JavaScript成为全球标准，几个公司联合ECMA（European Computer Manufacturers Association）组织定制了JavaScript语言的标准，被称为ECMAScript标准。

所以简单说来就是，ECMAScript是一种语言标准，而JavaScript是网景公司对ECMAScript标准的一种实现。


不过大多数时候，我们还是用JavaScript这个词。如果你遇到ECMAScript这个词，简单把它替换为JavaScript就行了。

JavaScript本身有很多设计缺陷，JavaScript的标准——ECMAScript在不断发展从而逐渐弥补一开始的设计缺陷。 最新版ECMAScript 6标准（简称ES6,别名ES2015）已经在2015年6月正式发布了,ES7标准也已经制定了。

>做微信小程序需要学什么

微信小程序一开始并不支持ES6,后来通过ES6转ES5的功能兼容了ES6语法,如图3-1所示。
![](/assets/图3-1.png)
不同于开发网页,我们开发微信小程序基本上都是使用JS核心语法,有些和网页开发相关的语法并不能在小程序中使用。虽然JavaScript一直在升级,但是核心语法并没有什么变化。

学习微信小程序主要需要学会JS核心语法，这也是本书着重介绍的。