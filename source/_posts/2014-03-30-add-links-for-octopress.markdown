---
layout: post
title: "为Octopress增加博客链接"
date: 2014-03-30 10:16:12 -0700
comments: true
categories: Octopress
tags: octopress
---

## 酷站博客

你有一些经常去的网站、博客，想推荐给大家，则可以在侧边栏加上一个“酷站博客” ，当然名字你自己取即可。

在 `source/_includes/custom/asides` 创建 `blog_link.html` ，代码如下：

{% raw %}

```html
<section>
<h1>酷站博客</h1>
<ul>
        <li>
        <a href="http://blog.jobbole.com/">伯乐在线</a>
        </li>
        <li>
        <a href="http://www.csdn.net/">CSDN</a>
        </li>
        <li>
        <a href="http://www.cnblogs.com/">博客园</a>
        </li>
        <li>
        <a href="http://coolshell.cn/">酷壳CoolShell</a>
        </li>
        <li>
        <a href="http://www.cnblogs.com/Solstice/">陈硕</a>
        </li>
</ul>
</section>
```

{% endraw %}


可以自行添加喜爱网站，然后在default_asides中加入`custom/asides/blog_link.html`