---
layout: post
title: "为Octopress添加统计"
date: 2014-03-10 11:24:42 +0000
comments: true
categories: Octopress
tags: octopress, statistics
---


## 使用Google Analytics统计工具

#### 注册Google Analytics账号

到[Google Analytics](http://www.google.com/analytics/ "Google Analytics")注册Analytics，获得一个google_analytics_tracking_id，添加到`_config`.yml中对应位置，并对网站进行验证即可

#### 验证Google Analytics

对自己的网站进行验证，只需将网站提供的用于验证的代码添加到`source/_includes/head.html`的`<head>`标签之间，网站部署到网上后，过几分钟即可验证通过，其他 需要验证的也同样操作。

	注意：如果head中有include google-analitics.html，这一步就不需要了

## 使用CNZZ统计工具

#### 注册CNZZ账号

到[CNZZ](http://zhanzhang.cnzz.com/ "CNZZ")注册一个账号。注册后，添加并验证你的网站就可以添加统计代码了

#### 验证CNZZ

选好自己喜欢的样式，获得代码，可添加到`source/_includes/custom/footer.html`中。即可查看每天你的博客的流量，进行相应的优化了。

