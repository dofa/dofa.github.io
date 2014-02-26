---
layout: post
title: "TCP/IP协议学习系列之三 — 链路层"
date: 2013-08-01 14:25:52 +0000
comments: true
tags: tcpip
categories: Embedded
---


### TCP/IP支持多种不同的链路层协议

这取决于网络所使用的硬件，如以太网、令牌环网、FDDI（光纤分布式数据接口）及RS-232串行线路等。

### 以太网是当今TCP/IP采用的主要的局域网技术

它采用一种称作CSMA/CD的媒体接入方法，其意思是带冲突检测的载波侦听多路接入（Carrier Sense, Multiple Access with Collision Detection）。它的速率为10 Mb/s，地址为48 bit。

### 以太网IP数据报的封装

以太网IP数据报的封装是在RFC 894[Hornig 1984]中定义的，但存在另外一个IEEE 802规格RFC 1042[Postel and Reynolds 1988]，只是大多数人采用RFC 894。RFC 894在有的地方称作Ethernet-II。

### SLIP和PPP

串行线路IP–SLIP和他的升级版PPP使用RS-232串口传数据，速度太慢，基本上大家都不用这种方式了，而改用宽带上网。这年头问别人如何上网，都是“你家多少兆？”。

### 环回接口

下面再来看一个大家都熟悉的ip：127.0.0.1。这个IP称作环回接口，它还有个英文名localhost。基本上，对这个ip的访问就是访问自己的主机。

### MTU

以太网一次可以传送的最大传输单元（MTU）为1500B。 


