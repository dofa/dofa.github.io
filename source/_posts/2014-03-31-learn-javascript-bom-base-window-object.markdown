---
layout: post
title: "JavaScript学习--BOM基础之window对象(转)"
date: 2014-03-31 08:26:06 -0700
comments: true
categories: Javascript
tags:  javascript, BOM
---

## 什么是 `BOM`

* `BOM`是`browser object model`的缩写，简称浏览器对象模型
* `BOM`提供了独立于内容而与浏览器窗口进行交互的对象
* 由于`BOM`主要用于管理窗口与窗口之间的通讯，因此其核心对象是`window`
* `BOM`由一系列相关的对象构成，并且每个对象都提供了很多方法与属性
* `BOM`缺乏标准，`JavaScript`语法的标准化组织是`ECMA`，`DOM`的标准化组织是`W3C`
* `BOM`最初是`Netscape`浏览器标准的一部分

## BOM结构图

{% img /image/web/browser_objects.png %}

window对象是BOM的顶层(核心)对象，所有对象都是通过它延伸出来的，也可以称为window的子对象。

由于window是顶层对象，因此调用它的子对象时可以不显示的指明window对象，例如下面两行代码是一样的：

	document.write("blog.dofa.org");
	window.document.write("blog.dofa.org");

## 全局的window对象

window对象是BOM中所有对象的核心

#### JavaScript中的任何一个全局函数或变量都是window的属性

	var sTest="dofa";
	document.write(sTest==window.sTest);

结果：

	true	

由于sTest是全局变量，因此可以通过window.sTest访问这个变量

#### window与self对象

self对象与window对象完全相同，self通常用于确认就是在当前的窗体内

#### window的子对象

* JavaScript document 对象
* JavaScript frames 对象
* JavaScript history 对象
* JavaScript location 对象
* JavaScript navigator 对象
* JavaScript screen 对象

