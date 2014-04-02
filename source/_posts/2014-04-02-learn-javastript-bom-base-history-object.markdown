---
layout: post
title: "JavaScript学习--BOM基础之history对象"
date: 2014-04-02 23:00:06 -0700
comments: true
categories: Javascript
tags:  javascript, BOM
---

History用于窗体中的导航

## History对象

* `history`对象是`window`对象的属性
* 浏览者通常可以使用浏览器的前进与后退按钮访问曾经浏览过的页面。`JavaScript`的`history`对象记录了用户曾经浏览过的页面，并可以实现浏览器前进与后退相似的导航功能
* 可以通过`back`函数后退一个页面，`forward`函数前进一个页面，或者使用`go`函数任意后退或前进页面，还可以通过`length`属性查看`history`对象中存储的页面数



## History对象函数

* `JavaScript` `history.go()` 函数 -- 前进或后退指定的页面数
* `JavaScript` `history.back()` 函数 -- 后退一页
* `JavaScript` `history.forward()` 函数 -- 前进一页

## History对象属性

* `JavaScript` `length` 属性 -- `history`对象中缓存了多少个`URL`


