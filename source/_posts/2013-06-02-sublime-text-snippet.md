---
layout: post
title: "Sublime Text的snippet"
date: 2013-06-02 14:25:52 +0000
comments: true
tags: sublime-text
categories: SublimeText
---

## snippet强大的自动补全功能

以前理解代码自动补全以为就是函数或变量的自动补全，其实还可以是代码块的自动补全。接触过sublime text后才发现si的自动补全弱爆了，si也就阅读代码方便，写代码以后还要靠sublime text。话说sublime text的snippet就是自动补全，我也是今天才知道snippet。在简单的接触后，马上就可以实现自己的自动补全，不得不说st2真乃coding神器！

## Example：for语句的补全

当匹配到`for`后，

{% img /imgage/embeded/snippet-for.jpg %}
输入`tab`，这时st2帮你输入以下代码：
{% img /imgage/embeded/snippet-for-tab.jpg %}
当前光标会停留在`count`上，继续key字就会把`count`替换掉，接着按下`tab`会把`i`也替换掉。
## 自定义snipppet
通过`tools`--> `New snippet`，会出现：

{% raw %}
```xml
<snippet>
	<content><![CDATA[
Hello, ${1:this} is a ${2:snippet}.
]]></content>
	<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
	<!-- <tabTrigger>hello</tabTrigger> -->
	<!-- Optional: Set a scope to limit where the snippet will trigger -->
	<!-- <scope>source.python</scope> -->
</snippet>
```
{% endraw %}

修改这行`<!-- <tabTrigger>hello</tabTrigger> -->`为`<tabTrigger>hello</tabTrigger>`就可以使用`hello+tab`调出`Hello, ${1:this} is a ${2:snippet}.`。光标首先会出现在`${1}`的位置上，`:this`表示`${1}`的默认值为`this`。

这里再给一个doxygen格式snippet配置：

{% raw %}
```xml
<snippet>
	<content><![CDATA[
/*!
 * \file ${1:file.c}
 * \brief this is a ${2:description} file
 * \author bitbegin
 * \date ${3:2013-6-3}
 * \version V1.0.061
 * \note this is a ${2:description} file
 * \warning Only for bitbegin
 * \details
 * ${4:your details}
 *
 */
]]></content>
	<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
	<tabTrigger>doxy-file</tabTrigger>
	<!-- Optional: Set a scope to limit where the snippet will trigger -->
	<!-- <scope>source.python</scope> -->
</snippet>
```
{% endraw %}
