---
layout: post
title: "使用PHP-FPM安装php5 server"
date: 2014-03-03 13:51:40 +0000
comments: true
categories: Server
tags: php5
---

## 安装环境

* nginx

* mysql

## 使用`PHP-FPM`安装php5 server

	apt-get install php5-fpm

> PHP-FPM is a daemon process (with the init script /etc/init.d/php5-fpm) that runs a FastCGI server on the socket /var/run/php5-fpm.sock.

## 配置nginx

```
[...]
worker_processes  4;
[...]
    keepalive_timeout   2;
[...]
```

## 网站配置

	vim /etc/nginx/sites-available/yoursite

## PHP配置

	vim /etc/php5/fpm/php.ini

set cgi.fix_pathinfo=0:

```
[...]
; cgi.fix_pathinfo provides *real* PATH_INFO/PATH_TRANSLATED support for CGI.  PHP's
; previous behaviour was to set PATH_TRANSLATED to SCRIPT_FILENAME, and to not grok
; what PATH_INFO is.  For more information on PATH_INFO, see the cgi specs.  Setting
; this to 1 will cause PHP CGI to fix its paths to conform to the spec.  A setting
; of zero causes PHP to behave as before.  Default is 1.  You should fix your scripts
; to use SCRIPT_FILENAME rather than PATH_TRANSLATED.
; http://php.net/cgi.fix-pathinfo
cgi.fix_pathinfo=0
[...]
```

## Server Reload

	/etc/init.d/nginx -s reload
	/etc/init.d/php5-fpm reload

