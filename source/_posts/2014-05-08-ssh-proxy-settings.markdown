---
layout: post
title: "ssh代理设置"
date: 2014-05-08 20:28:50
comments: true
categories: Shell
tags: ssh, putty, plink
---

有两种方式实现ssh代理，一种是ssh命令行，另外一种使用putty的plink工具。

## ssh命令行

	ssh -qTfnN -D 8087 用户名@远程ssh主机名

上面的8087是本地未被占用的端口，可以自己选择。其它参数的意思是：

	-q :- be very quite, we are acting only as a tunnel.
	-T :- Do not allocate a pseudo tty, we are only acting a tunnel.
	-f :- move the ssh process to background, as we don’t want to interact with this ssh session directly.
	-N :- Do not execute remote command.
	-n :- redirect standard input to /dev/null.	

#### remote端口占用

	sudo netstat -antpl  | grep ssh

`kill`进程

	sudo kill -9 xxxx


## plink工具

	plink -C -D 127.0.0.1:8087 -N -pw 密码 用户名@远程ssh主机名 

