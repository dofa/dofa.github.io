---
layout: post
title: "常用git设置"
date: 2014-05-08 20:52:50
comments: true
categories: Git
tags: git
---


## Git基本配置

	git config --global user.name 'dofa'
	git config --global user.email 'xxx@xxx.com'


## Git使用代理

	git config --global http.proxy http://127.0.0.1:8087
	git config --global https.proxy http://127.0.0.1:8087
	git config --global http.sslverify false

`http.sslverify`设置为`false`可以加快同步速度。

## Git显示漂亮日志

	git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"
	