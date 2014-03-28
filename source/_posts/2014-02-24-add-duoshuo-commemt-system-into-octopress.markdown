---
layout: post
title: "为 Octopress 添加多说评论系统"
date: 2014-02-24 08:49:29 +0000
comments: true
tags: octopress
categories: Octopress
---


disqus是国外的评论系统，速度实在太慢，使用duoshuo会比较好
## 修改配置

在_config.yml中注释掉有关disqus的配置，增加：

```
# duoshuo comments
duoshuo_comments: true
duoshuo_short_name: yourname
```

## 修改post模板

在 `source/_layouts/post.html` 中的 disqus代码下下方添加多说评论模块

{% raw %}
```html
{% if site.duoshuo_short_name and site.duoshuo_comments == true and page.comments == true %}
  <section>
    <h1>Comments</h1>
    <div id="comments" aria-live="polite">{% include post/duoshuo.html %}</div>
  </section>
{% endif %}
```
{% endraw %}

## 增加duoshuo模板

创建一个 `source/_includes/post/duoshuo.html`

{% raw %}
```html
<!-- Duoshuo Comment BEGIN -->
<div class="ds-thread" data-title="{% if site.titlecase %}{{ post.title | titlecase }}{% else %}{{ post.title }}{% endif %}"></div>
<script type="text/javascript">
  var duoshuoQuery = {short_name:"{{ site.duoshuo_short_name }}"};
  (function() {
    var ds = document.createElement('script');
    ds.type = 'text/javascript';ds.async = true;
    ds.src = 'http://static.duoshuo.com/embed.js';
    ds.charset = 'UTF-8';
    (document.getElementsByTagName('head')[0] 
    || document.getElementsByTagName('body')[0]).appendChild(ds);
  })();
</script>
<!-- Duoshuo Comment END -->
```
{% endraw %}
