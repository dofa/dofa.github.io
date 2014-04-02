---
layout: post
title: "JavaScript学习--BOM基础之location对象"
date: 2014-04-02 23:10:06 -0700
comments: true
categories: Javascript
tags:  javascript, BOM
---

Location用于获取或设置窗体的URL，并且可以用于解析URL，是BOM中最重要的对象之一

## Location对象

* `Location`既是`window`对象的属性又是`document`对象的属性
* `location`包含8个属性，其中7个都是当前窗体的`URL`的一部分，剩下的也是最重要的一个是`href`属性，代表当前窗体的`URL`
* `location`的8个属性都是可读写的，但是只有`href`与`hash`的写才有意义。例如改变`location.href`会重新定位到一个`URL`，而修改`location.hash`会跳到当前页面中的`anchor(<a id="name">`或者`<div id="id">`等)名字的标记(如果有)，而且页面不会被重新加载

## 示例

	document.write(window.location==document.location);

## Location对象属性图示

{% img /image/web/window_location.png %}


location属性

* `JavaScript` `hash` 属性	--	返回`URL`中`#`符号后面的内容
* `JavaScript` `host` 属性	--	返回域名
* `JavaScript` `hostname` 属性	--	返回主域名
* `JavaScript` `href` 属性	--	返回当前文档的完整`URL`或设置当前文档的`URL`
* `JavaScript` `pathname` 属性	--	返回`URL`中域名后的部分
* `JavaScript` `port` 属性	--	返回`URL`中的端口
* `JavaScript` `protocol` 属性	--	返回`URL`中的协议
* `JavaScript` `search` 属性	--	返回`URL`中的查询字符串
* `JavaScript` `assign()`	函数 --	设置当前文档的`URL`
* `JavaScript` `replace()` 函数 --	设置当前文档的`URL`，并在`history`对象的地址列表中删除这个`URL`
* `JavaScript` `reload()`	函数 --	重新载入当前文档(从`server`服务器端)
* `JavaScript` `toString()` 函数 --	返回`location`对象`href`属性当前的值


Note: 主域名是不带www的域名，例如dreamdu.com，主域名前面带前缀的通常都为二级域名或多级域名，例如www.dreamdu.com其实是二级域名。



