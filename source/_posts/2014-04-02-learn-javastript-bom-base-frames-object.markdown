---
layout: post
title: "JavaScript学习--BOM基础之frames对象"
date: 2014-04-02 22:35:06 -0700
comments: true
categories: Javascript
tags:  javascript, BOM
---

Frames用于表现HTML页面当前窗体的中的框架集合

## Frames对象

* `frames`对象是`window`对象的属性
* 如果页面使用框架，将产生一个框架集合`frames`，在集合中可用数字(从0开始，从左到右，逐行索引)或名字索引框架

## 框架集引用中使用的对象

对象 | 位置
:----------|:------------
window | 当前框架
top | 最顶层的框架，就是浏览器窗体
parent | 包含当前框架的父框架
self | 当前框架，总是等于window对象

## 示例

<% raw %>
```html
<frameset rows="20%, *, 20%">
        <frame src="http://www.dreamdu.com/javascript/exe_window.frames.top/" name="top" />
        <frameset cols="20%, *">
                <frame src="http://www.dreamdu.com/javascript/exe_window.frames.top/" name="left" />
                <frame src="http://www.dreamdu.com/javascript/exe_window.frames.right/" name="right" />
        </frameset>
        <frame src="http://www.dreamdu.com/javascript/exe_window.frames.top/" name="bottom" />
</frameset>
```
<% endraw %>

上面的框架页示例产生了一个框架集

`window`与`self`代表相同的对象，但是`self`是为了确定正在使用的框架不是`parent`，而是自身,`top`对象代表最顶层框架，浏览器窗体本身，因此在这个例子中就等于`window`对象,如果页面上没有框架，`window`，`self`都等于`top`，并且框架集合的长度为0

如果框架名称为`right`的页面包括下面框架：

<% raw %>
```html
<frameset cols="50%, *">
        <frame src="http://www.dreamdu.com/javascript/exe_window.frames.top/" name="righttop" />
        <frame src="http://www.dreamdu.com/javascript/exe_window.frames.top/" name="rightbottom" />
</frameset>
```
<% endraw %>

那么righttop与rightbottom的parent父框架为right
