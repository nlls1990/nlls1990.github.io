---
layout: post
title:  "0921 - wtfjs"
date:   2017-09-21 13:40:29 +0800
category: 翻译
excerpt: JavaScript 有趣和棘手（坑爹？）的示例
---



## 动机

>Just for Fun
-- "Just for Fun: The Story of an Accidental Revolutionary", Linus Torvalds

本文所罗列出来的内容的最终目的是整理和收集那些疯狂的例子, 同时对它们进行解释和说明它们是怎么运行的. 仅仅是出于对学习那些我们以前所不知道的东西的乐趣.

如果你是一个小白, 你可以用这些笔记去深入学习JavaScript. 我希望这些例子可以激发你去投入更多的时间去了解这些特性.

如果你是一个专业的开发者, 你可以思考下这些例程, 并以这些奇异且令人难以想象到的挚爱的JavaScript作为参考.

不管怎样, 去读读它吧. 你很有可能会发现某些新东西呢.


## 标记

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


## 示例



### `[]`等于`![]`

数组等于非数组:
```javascript
[] == ![] // -> true
```
**解释**
> * [12.5.9 Logical NOT Operator (!)](https://www.ecma-international.org/ecma-262/#sec-logical-not-operator)
> * [7.2.13 Abstract Equality Comparison](https://www.ecma-international.org/ecma-262/#sec-abstract-equality-comparison)



### true 等于 false

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

### baNaNa

```javascript
'b' + 'a' + + 'a' + 'a'
```

这句代码是学校里的很古老的一个JavaScript的笑话, 但是值得重新提起. 如下是最原始的例子:
```javascript
'foo' + + 'bar' // -> 'fooNaN'
```
**解释**
这个表达式可以等效为 `'foo' + (+'bar')`, `'bar'`转化的结果并不是一个数字

> * [12.8.3 The Addition Operator (+)](https://www.ecma-international.org/ecma-262/#sec-addition-operator-plus)
> * [12.5.6 Unary + Operator](https://www.ecma-international.org/ecma-262/#sec-unary-plus-operator)

### `NaN` is not a `NaN`

```javascript
NaN === NaN // ->false
```
**解释**
规范中严格说明了这个行为背后的逻辑

>1. 如果 Type(x)和 Type(y)不同, 那么返回false.
>2. 如果 Type(x) 是一个数字类型, 那么,
>  i. 如果 x 是 NaN, 那么返回false.
>  ii. 如果 y 是 NaN, 那么返回false.
>  iii. ...
>
>  [7.2.14 Strict Equality Comparison](https://www.ecma-international.org/ecma-262/#sec-strict-equality-comparison)
如下是来自IEEE对于NaN的解释:
>Four mutually exclusive relations are possible: less than, equal, greater than, and unordered. The last case arises when at least one operand is NaN. Every NaN shall compare unordered with everything, including itself.
> -- "[What is the rationale for all comparisons returning false for IEEE754 NaN values?](https://stackoverflow.com/questions/1565164/what-is-the-rationale-for-all-comparisons-returning-false-for-ieee754-nan-values#1573715)" at StackOverflow
> 

### It's a fail
你可能不会相信, 但是...

```javascript
(![]+[])[+[]]+(![]+[])[+!+[]]+([![]]+[][[]])[+!+[]+[+[]]]+(![]+[])[!+[]+!+[]]
// -> 'fail'
```

**解释**
通过切割大块的符号为片段, 我们可以看到如下模式会生成如下:

```javascript
(![]+[]) // -> 'false'
![]      // -> false
```

因此我们尝试添加中括号[]为false. 然而因为大量的内部函数调用(binary + Operator -> ToPrimitive -> [[DefaultValue]]), 我们以转化后的右端操作符为字符串:

```javascript
(![]+[].toString()) // 'false'
```

思考一下, 一个字符串作为一个数组, 我们通过加入索引来访问第一个字母:

```javascript
'false'[0] // -> 'f'
```
剩余的字符就很明显了,当超过字符的总数时, 索引i返回的就是'falseundefined', 例如我们去访问index['10'].


[原文链接](https://github.com/denysdovhan/wtfjs)