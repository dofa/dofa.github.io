---
layout: post
title: "安装shadowsocks-nodejs"
date: 2014-05-13 21:18:30
comments: true
categories: Server
tags: nodejs, shadowsocks
---

## 安装shadowsocks包

	npm install -g shadowsocks

## 创建 `config.json`

	{
	    "server":"yourip or yourdomain",
	    "server_port":8388,
	    "local_port":1080,
	    "password":"xxxxxx",
	    "timeout":600,
	    "method":"rc4",
	    "local_address":"127.0.0.1"
	}

## 安装`coffee-script`

	npm install -g coffee-script

## 后台运行

	sudo nohup ssserver > log &

## `local`端运行

	sslocal

