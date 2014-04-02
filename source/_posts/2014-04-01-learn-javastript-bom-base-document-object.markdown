---
layout: post
title: "JavaScript学习--BOM基础之document对象"
date: 2014-04-01 08:35:06 -0700
comments: true
categories: Javascript
tags:  javascript, BOM
---

Document用于表现HTML页面当前窗体的内容

## Document对象

* `document`是`BOM`中最重要对象之一
* `document`对象是`window`对象的属性
* `document`对象包含一个节点对象，此对象包含每个单独页面的所有`HTML`元素，这就是W3C的`DOM`对象

## Document属性

* `cookie` --	用户`cookie`
* `title`	--	当前页面`title`标签中定义的文字
* `URL`	--	当前页面的`URL`

下面内容的不建议使用

* `alinkColor`	--	代表`HTML body`标签的`alink`属性
* `bgColor` --	代表`HTML body`标签的`bgcolor`属性
* `fgColor` --	代表`HTML body`标签的`text`属性
* `linkColor` --	代表`HTML body`标签的`link`属性
* `vlinkColor`	--	代表`HTML body`标签的`vlink`属性
* `lastModified`	-- 页面最后修改的日期字符串，可以使用`Date`的构造函数转换为日期，例如：`new Date(document.lastModified);`
* `referrer`	--	浏览器`history`中后退一个位置的`URL`

由于document代表HTML文档的内容，因此可以通过它表示文档中加载的一些元素，这些元素全部通过集合访问。

* `anchors`	--	文档中所有锚(a name="aname")的集合
* `applets`	--	文档中所有`applet`标签表示的内容的集合
* `embeds`	--	文档中所有`embed`标签表示的内容的集合
* `forms`	--	文档中所有`form`标签表示的内容的集合
* `images`	--	文档中所有`image`标签表示的内容的集合
* `links`	-- 文档中所有`a`(链接)标签表示的内容的集合


## Document函数

* `JavaScript` `write()` 函数
* `JavaScript` `writeln()` 函数
* `JavaScript` `document.open()` 函数
* `JavaScript` `document.close()` 函数

## 使用document索引页面内的元素

可以使用数字或名称索引页面中的元素集合，每个元素的属性都变成了集合中相应对象的属性。

{% raw %}

```html
<form name="form1"><a href="http://www.dreamdu.com/xhtml/" name="a1">xhtml</a></form>
<form name="form2"><a href="http://www.dreamdu.com/css/" name="a2">css</a></form>
<form name="form3"><a href="http://www.dreamdu.com/javascript/" name="a3">javascript</a></form>

<input type="button" value="显示第二个表单的名称" onclick="alert(document.forms[1].name)" />
<input type="button" value="显示第二个表单的名称第二种方法" onclick="alert(document.forms['form2'].name)" />
<input type="button" value="显示第三个链接的名称" onclick="alert(document.links[2].name)" />
<input type="button" value="显示第三个链接的名称第二种方法" onclick="alert(document.links['a3'].name)" />
<input type="button" value="显示第三个链接href属性的值" onclick="alert(document.links[2].href)" />
```

{% endraw %}

表示第二个表单的方法：`document.forms[1]或document.forms["form2"]`

表示第三个链接的方法：`document.links[2]或document.links["a3"]`

表示第三个链接`href`属性的方法：`document.links[2].href`

