---
layout: post
title: "把Octopress从github搬到gitcafe"
date: 2014-03-29 01:49:00 -0700
comments: true
categories: Octopress
tags: octopress, github, gitcafe
---

其实找就想把`octopress`博客从`github`搬到`gitcafe`了，因为国内访问`github`的速度实在慢，而且还不时被墙。比如，今天不翻墙就无法访问了。

我采用了比较笨的方法：原本的东西都不需要改动，在一个新的文件夹下 *clone github master* 分支，增加 *gitcafe remote*，然后`push`到`gitcafe`的`gitcafe-pages`分支上。

## clone github master

这个是`rake deploy`到`github`上去的文件。

## 增加remote

	git remote addd gitcafe git@gitcafe.com:xx/xx

## push到gitcafe

	git push gitcafe gitcafe-pages

## 注意事项

#### 在gitcafe上增加ssh密钥

否则git无法连接

#### 把指向github的域名改到gitcafe上去

这样方便再次迁移

	