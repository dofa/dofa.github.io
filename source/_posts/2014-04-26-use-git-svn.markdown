---
layout: post
title: "使用git-svn"
date: 2014-04-26 14:38:50
comments: true
categories: Git
tags: git, svn
---

个人比较习惯git，无奈目前单位使用svn，尽管svn相当不好用。今天查找了一下解决方法，本地使用git，服务器为svn类型。

## 从svn clone出项目

	git svn clone -s https://svn.xxx.com/svn/xxx
	git svn show-ignore >> .git/info/exclude 

## 建立本地工作分支

	git checkout -b work 

现在可以正常使用git命令了

## 提交回svn的过程

	git checkout master  
	git merge work  
	git svn rebase  
	git svn dcommit 

## 冲突解决

	git svn rebase 

提示有冲突，手动解决冲突，然后：

	git add .
	git rebase --continue
	git svn dcommit

执行后，发现本地的commit也跟server上的有同步。
