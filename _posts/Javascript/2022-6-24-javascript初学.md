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

## 1. script标签中的JS

```html
<script type="text/javascript">
    //JS code
    alert("This my first JS code!");
</script>
```

## 2. 标签属性中的JS

```html
<button onclick="alert('hello');">我是按钮</button>  
<a href="javascript:alert('aaa');">超链接</a>  
```

## 3. 外部文件中的JS

JS代码可以写到外部文件中，文件一般以".js"为后缀名，在script标签中引用

```html
<script type="text/javascript" src="文件路径">
//引用外部js时，此处的代码不会起作用，会被自动忽略
//如需增加网页内部JS，须另外新建一个script标签
</script>  
```

# 输出

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

## 1.  ... 
# 字面量

