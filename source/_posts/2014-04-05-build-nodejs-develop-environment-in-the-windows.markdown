---
layout: post
title: "在Windows环境下搭建nodejs环境"
date: 2014-04-05 18:58:25 -0700
comments: true
categories: Nodejs
tags: nodejs
---


## Windows环境下安装nodejs环境

* 到`http://nodejs.org/download/`下载最新版本的windows安装程序，目前是`v0.10.26`

* `v0.10.26`版本默认已经安装`npm`，并添加了`PATH`

* 命令行下测试`node`和`npm`（注意系统要更新环境变量，在`CMD`下执行`PATH=c:\`退出即可）


## 包安装

在项目文件下执行：

	npm install

## 有用的命令

	npm start : start a local development web-server
	npm test : start the Karma unit test runner
	npm run protractor : run the Protractor end 2 end tests
	npm update-webdriver : install the drivers needed by Protractor

	