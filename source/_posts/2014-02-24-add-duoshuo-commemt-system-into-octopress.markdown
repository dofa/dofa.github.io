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

在 `source/_layouts/post.html` 中的 disqus代码下方添加多说评论模块

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

## 204-03-29更新

#### 为page增加评论功能

在 `source/_layouts/page.html` 中的disqus代码下方添加多说评论模块：

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

在 `_includes/article.html` 文件的disqus代码下方添加：

{% raw %}
```html
         {% if site.duoshuo_short_name and page.comments != false and post.comments != false and site.duoshuo_comments == true %}
          | <a href="{% if index %}{{ root_url }}{{ post.url }}{% endif %}#comments">Comments</a>
         {% endif %}
```
{% endraw %}

#### 为首页侧边栏插入最新评论

首先在 _config.yml 中再插入如下代码

    duoshuo_asides_num: 10      # 侧边栏评论显示条目数
    duoshuo_asides_avatars: 0   # 侧边栏评论是否显示头像
    duoshuo_asides_time: 0      # 侧边栏评论是否显示时间
    duoshuo_asides_title: 0     # 侧边栏评论是否显示标题
    duoshuo_asides_admin: 0     # 侧边栏评论是否显示作者评论
    duoshuo_asides_length: 18   # 侧边栏评论截取的长度

再创建 `_includes/custom/asides/recent_comments.html`

{% raw %}
```html
<section>
<h1>Recent Comments</h1>
<ul class="ds-recent-comments" data-num-items="{{ site.duoshuo_asides_num }}" data-show-avatars="{{ site.duoshuo_asides_avatars }}" data-show-time="{{ site.duoshuo_asides_time }}" data-show-title="{{ site.duoshuo_asides_title }}" data-show-admin="{{ site.duoshuo_asides_admin }}" data-excerpt-length="{{ site.duoshuo_asides_length }}"></ul>
{% if index %}
<!--多说js加载开始，一个页面只需要加载一次 -->
<script type="text/javascript">
  var duoshuoQuery = {short_name:"{{ site.duoshuo_short_name }}"};
  (function() {
    var ds = document.createElement('script');
    ds.type = 'text/javascript';ds.async = true;
    ds.src = 'http://static.duoshuo.com/embed.js';
    ds.charset = 'UTF-8';
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(ds);
  })();
</script>
<!--多说js加载结束，一个页面只需要加载一次 -->
{% endif %}
</section>
```
{% endraw %}

最后，_confit.yml 中的 blog_index_asides 行或 page_asides 行或 post_asides 添加:

    custom/asides/recent_comments.html

    