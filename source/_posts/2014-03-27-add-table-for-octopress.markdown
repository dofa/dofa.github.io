---
layout: post
title: "Octopress表格设置"
date: 2014-03-27 14:50:05 +0000
comments: true
categories: Octopress
tags: octopress
styles: [data-table]
---


Octopress默认的表格没有边框，比较难看。需要增加一个css。

## 添加样式*css*

新建一个 *data-table.css*，放到*source/stylesheets*下面

{% raw %}
```
table th, table td {
  border-style:dashed;
  border-width:1px;
  border-color:#007eff;
  padding-left: 3px;
  padding-right: 3px;
}
 
table th {
  border-style:solid;
  font-weight:bold;
  background-color:#d2e8ff;
}

table tr:hover{
    background-color:#c4e4fe;
} 

table th[align="left"], table td[align="left"] {
  text-align:left;
}
 
table th[align="right"], table td[align="right"] {
  text-align:right;
}
 
table th[align="center"], table td[align="center"] {
  text-align:center;
}
```
{% endraw %}

## 包含样式

在*source/_includes/head.html*增加如下代码：

{% raw %}
```
<link href="{{ root_url }}/stylesheets/screen.css" media="screen, projection" rel="stylesheet" type="text/css">
{% if page.styles contains 'data-table' %}
<link href="{{ root_url }}/stylesheets/data-table.css" media="screen, projection" rel="stylesheet" type="text/css" />
{% endif %}
```
{% endraw %}

## 在需要该样式的post中增加

	styles: [data-table]

即可。

## 表格写法

	左对齐表头 | 中间对齐表头 | 右对齐表头
	:----------|:------------:|----------:
	左对齐数据 |中间对齐数据  |右对齐数据
	第二行数据 |也是第二行    |还是第二行
	懒得写了...|.....         |.....
	长数据，以便看出表头的对齐|长数据，以便看出表头的对齐|长数据，以便看出表头的对齐

生成表格：

左对齐表头 | 中间对齐表头 | 右对齐表头
:----------|:------------:|----------:
左对齐数据 |中间对齐数据  |右对齐数据
第二行数据 |也是第二行    |还是第二行
懒得写了...|.....         |.....
长数据，以便看出表头的对齐|长数据，以便看出表头的对齐|长数据，以便看出表头的对齐