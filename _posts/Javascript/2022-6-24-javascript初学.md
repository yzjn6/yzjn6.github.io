---
layout: post
title: Day0-JS的引入
categories: [Javascript]
description: JS
keywords: JS, JavaScript
---

# JavaScript

## 介绍

JavaScript是 Web 的编程语言。

所有现代的 HTML 页面都可以使用 JavaScript。

## JS的特点

- 解释型语言
- 类似于C和Java的语法结构
- 动态语言
- 基于原型的面向对象

# JS的编写位置

与CSS类似，JS也有对应的三种引入方式

## 1. script标签包裹的JS（内部样式）

```html
<script type="text/javascript">
    //JS code
    alert("This my first JS code!");
</script>
```

## 2. 标签属性中的JS（内联样式）

```html
<button onclick="alert('hello');">我是按钮</button>  
<a href="javascript:alert('aaa');">超链接</a>  
```

## 3. 外部文件中的JS（ 外部样式）

JS代码可以写到外部文件中，文件一般以".js"为后缀名，在script标签中引用

```html
<script type="text/javascript" src="文件路径">
//引用外部js时，此处的代码不会起作用，会被自动忽略
//如需增加网页内部JS，须另外新建一个script标签
</script>  
```

 外部样式可以在多个页面中使用

# 常用输出

## 1. 弹窗

```javascript
alert("xxxxxx");
```

该语句会在浏览器窗口中弹出一个警告框

## 2. 网页中

```js
document.write("xxxxxx");
```

该内容将会被输出至body标签中，并在页面中显示

## 3. 控制台

```js
console.log("xxxxxxxx");
```

该内容会被输出至开发者工具的控制台中



# 基本语法

1. JS严格区分大小写
2. JS每一条语句要以`;`结尾，如果不写会影响浏览器性能或加错分号
3. JS会自动忽略空格与换行，可以利用空格与换行对代码进行格式化，提高易读性

# 注释

正确的注释可以提高代码的易读性，方便自己或他人理解代码

### 多行注释

```js
/*
注释区
*/
```

### 单行注释

```js
//注释区
```
