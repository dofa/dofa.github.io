---
layout: post
title: "Debian7 Wheezy 镜像源的配置"
date: 2014-03-09 08:13:15 +0000
comments: true
categories: Server
tags: debian, wheezy
---


debian update或install package使用国内源会非常慢，一般我们使用163源。
简单的说有两种方法修改源，我们直接使用第二种方法。

---

## 方法1：增加163源

以Squeeze为例, 编辑/etc/apt/sources.list文件, 在文件最前面添加以下条目(操作前请做好相应备份)

    deb http://mirrors.163.com/debian/ squeeze main non-free contrib
    deb http://mirrors.163.com/debian/ squeeze-proposed-updates main non-free contrib
    deb-src http://mirrors.163.com/debian/ squeeze main non-free contrib
    deb-src http://mirrors.163.com/debian/ squeeze-proposed-updates main non-free contrib

## 方法2：替换使用163的源

下载相应版本的sources.list, 覆盖/etc/apt/sources.list即可(操作前请做好相应备份)

	http://mirrors.163.com/.help/debian.html


## 使用新的源更新debian

	sudo apt-get update -y
	sudo apt-get upgrade -y
	sudo apt-get install sudo -y


## 更新失败时

注释掉下面的三行，删除也行

	#deb http://http.us.debian.org/debian wheezy main contrib non-free
	#deb http://non-us.debian.org/debian-non-US wheezy/non-US main contrib non-free
	#deb http://security.debian.org wheezy/updates main contrib non-free
