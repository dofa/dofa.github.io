---
layout: post
title: "JavaScript学习--BOM基础之navigator对象(转)"
date: 2014-04-03 21:52:06 -0700
comments: true
categories: Javascript
tags:  javascript, BOM
---

navigator对象通常用于检测浏览器与操作系统的版本

## Navigator对象

* `navigator`对象是`window`对象的属性
* 由于`navigator`没有统一的标准，因此各个浏览器都有自己不同的`navigator`版本，这里只介绍最普遍支持且最常用的

## 常用的navigator属性

* `appCodeName`	--	浏览器代码名的字符串表示
* `appName`	--	官方浏览器名的字符串表示
* `appVersion`	--	浏览器版本信息的字符串表示
* `cookieEnabled`	--	如果启用`cookie`返回`true`，否则返回`false`
* `javaEnabled`	--	如果启用`java`返回`true`，否则返回`false`
* `platform`	--	浏览器所在计算机平台的字符串表示
* `plugins`	--	安装在浏览器中的插件数组
* `taintEnabled`	--	如果启用了数据污点返回`true`，否则返回`false`
* `userAgent`	--	用户代理头的字符串表示


`navigator`中最重要的是`userAgent`属性，返回包含浏览器版本等信息的字符串，其次`cookieEnabled`也很重要，使用它可以判断用户浏览器是否开启`cookie`。
