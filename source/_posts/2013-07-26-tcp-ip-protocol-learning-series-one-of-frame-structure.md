---
layout: post
title: "TCP/IP 协议学习系列之一 — 帧结构（frame）"
date: 2013-07-26 14:25:52 +0000
comments: true
tags: tcpip
categories: Embedded
---


## TCP/IP协议封包

我觉得学习TCP/IP协议可以从它的封包开始，了解它在硬件上是怎么实现的是个不错的开端。

{% img /imgage/embeded/tcpip-package.bmp %}

上图是应用程序通过TCP/IP协议传输时的数据封包过程，该图基本反应了TCP/IP协议簇的数据打包过程。
封装好的IP协议一般通过硬件发送出去，比如Ethernet、令牌网、电话线。目前广泛应用的是Ethernet，我们的产品也不例外。

## Ethernet Frame结构

我们看下Ethernet的帧结构：

{% img /imgage/embeded/ethernet-frame.bmp %}

基本上就是在TCP/IP封包基础上增加了一个Ethernet Frame Header和Frame Tail(CRC)。

这里的DA和SA指的是MAC，固定为6字节。类型/长度在不同的协议规格下有不同意义，Ethernet-II要求不小于0×8000的类型码，IEEE 802规格定义该字段为报文数据的长度。
