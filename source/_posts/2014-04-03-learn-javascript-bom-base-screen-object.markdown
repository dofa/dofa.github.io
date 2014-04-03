---
layout: post
title: "JavaScript学习--BOM基础之screen对象(转)"
date: 2014-04-03 21:57:06 -0700
comments: true
categories: Javascript
tags:  javascript, BOM
---

screen对象用于获取用户的屏幕信息

## Screen对象

* `Screen`对象是`window`对象的属性


## Screen对象属性

* `JavaScript` `availHeight` 属性	--	窗口可以使用的屏幕高度，单位像素
* `JavaScript` `availWidth` 属性	--	窗口可以使用的屏幕宽度，单位像素
* `JavaScript` `colorDepth` 属性	--	用户浏览器表示的颜色位数，通常为32位(每像素的位数)
* `JavaScript` `pixelDepth` 属性	--	用户浏览器表示的颜色位数，通常为32位(每像素的位数)（`IE`不支持此属性）
* `JavaScript` `height` 属性	--	屏幕的高度，单位像素
* `JavaScript` `width` 属性	--	屏幕的宽度，单位像素

`availWidth`与`availHeight`属性非常有用，例如：可以使用下面的代码填充用户的屏幕：


	window.moveTo(0,0);
	window.resizeTo(screen.availWidth, screen.availHeight);