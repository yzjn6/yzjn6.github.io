---
layout: post
title: JS作用域
categories: [Javascript]
description: JS
keywords: JS, JavaScript
---





# 作用域

负责收集并维护由所有声明的标识符组成的一系列查询，并实施一套非常严格的规则，确定当前执行的代码对这些标识符的访问权限。

# LHS查询和RHS查询

> **LHS查询**：赋值操作左侧的查询，LHS查询试图找到变量的容器本身，从而对其赋值。
>
> 可以理解为 ：“赋值操作的目标是谁”

> **RHS查询**：赋值操作右侧的查询，可以理解为“取到某某的值”
>
> 可以理解为：“谁是赋值操作的源头“

## LHS查询

```js
a=2;
```

这里主要目的是找到一个容器来保存“`=2`”。

## RHS查询

```js
console.log(a);
```

这里a并没有赋予任何值。同时，需要查找并取得a的值，这样才能将值传递给console.log(..)。

> ## 例子

> ```js
> function foo(a) {
>     console.log(a);
> }
> 
> foo(2);
> ```

> ### LHS
>
> - 在调用函数过程中，给`a`赋值`2`。（已知`2`找到容器`a`，这里是一个隐式的赋值）
>
> ### RHS
>
> - foo(...)（找到函数`foo(...)`）
> - 函数内部console.log(...)（取得`console.log(...)`的最终结果）
> - console对象对`log`方法RHS查询
> - a（取得参数的值`2`）

> ## 例子

> ```js
> function foo(a) {
>   var b = a;
>   return a + b;
> }
> var c = foo(2);
> ```
>

> ### LHS
>
> - `var c =` foo(2);（赋值）
> - `var b =`a;（赋值）
> - `a=`2;（赋值）
>
> ### RHS
>
> - 查找foo(...)
> - var b = `a`;
> - return `a` + b;
> - return a + `b`;

