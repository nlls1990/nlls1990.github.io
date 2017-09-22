---
layout: post
title:  "0921 - wtfjs"
date:   2017-09-21 13:40:29 +0800
category: 翻译
excerpt: JavaScript 有趣和棘手（坑爹？）的示例
---

[原文链接](https://github.com/denysdovhan/wtfjs)

##动机

---
>Just for Fun
-- "Just for Fun: The Story of an Accidental Revolutionary", Linus Torvalds

---
本文所罗列出来的内容的最终目的是整理和收集那些疯狂的例子, 同时对它们进行解释和说明它们是怎么运行的. 仅仅是出于对学习那些我们以前所不知道的东西的乐趣.

如果你是一个小白, 你可以用这些笔记去深入学习JavaScript. 我希望这些例子可以激发你去投入更多的时间去了解这些特性.

如果你是一个专业的开发者, 你可以思考下这些例程, 并以这些奇异且令人难以想象到的挚爱的JavaScript作为参考.

不管怎样, 去读读它吧. 你很有可能会发现某些新东西呢.

---

##标记

---
`// ->`用于显示表达式的结果. 例如:
```javascript
1 + 1 // -> 2
```
`// >` 用于显示`console.log`或者其他的输出结果.例如:
```javascript
console.log('hello, world!') // > hello, world!
```
`//` 仅仅用于解释说明的注释.例如:
```javascript
// 定义一个foo常量函数
const foo = function () {}
```
---

##示例

---

###`[]`等于`![]`

数组等于非数组:
```javascript
[] == ![] // -> true
```
**解释**
> * [12.5.9 Logical NOT Operator (!)](https://www.ecma-international.org/ecma-262/#sec-logical-not-operator)
> * [7.2.13 Abstract Equality Comparison](https://www.ecma-international.org/ecma-262/#sec-abstract-equality-comparison)

---

###true 等于 false

```javascript
!!'false' == !!'true' // -> true
!!'false' === !!'true' // -> true
```
**解释**
请按如下步骤思考:
```javascript
// 真是真属性的元素, 而且代表值为1, 'true'在字符串表中是NaN类型.
true == 'true' // -> false
false == 'false' // -> false

// 'false'不是一个空字符串, 它是真属性的元素
!!'false' // -> true
!!'true' // -> true
```
> * [7.2.13 Abstract Equality Comparison](https://www.ecma-international.org/ecma-262/#sec-abstract-equality-comparison)

---

