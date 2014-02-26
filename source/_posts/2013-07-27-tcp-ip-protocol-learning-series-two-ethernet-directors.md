---
layout: post
title: "TCP/IP协议学习系列之二 — Ethernet控制器"
date: 2013-07-27 14:25:52 +0000
comments: true
tags: tcpip
categories: Embedded
---


## 硬件架构

前面讲了，处理TCP/IP封包的硬件主要使用Ethernet模块。
大多数Ethernet模块分为这几个部分：PHY，MAC，MII/RMII管理，DMA和控制器。


* PHY实现bit流到cat5的transfer
* MAC实现数据链路层的介质访问控制子层，并执行CSMA/CD功能
* MII/RMII提供访问PHY的接口给MAC使用
* DMA大家都懂得
* 控制器这里指的是协调MAC、MII/RMII管理、DMA的工具，不过一般也理解为Ethernet模块。比如PIC32中Ethernet控制器包括MAC、MII/RMII管理、DMA和SFR。


## 以太网原理—CSMA/CD

CS：载波侦听
在发送数据之前进行监听，以确保线路空闲，减少冲突的机会。
MA：多址访问
每个站点发送的数据，可以同时被多个站点接收。
CD：冲突检测
边发送边检测，发现冲突就停止发送，然后延迟一个随机时间之后继续发送。 

## 以太网发展简史

IEEE802.3 以太网标准
IEEE802.3u 100BASE-T快速以太网标准
IEEE802.3z/ab 1000Mb/s千兆以太网标准
IEEE802.3ae 10GE以太网标准

## 相关技术

#### 自协商技术

{% img /imgage/embeded/negotiation.bmp %}

#### 自适应技术： 智能MDI/MDIX

直连网线、交叉网线自动识别

#### 流量控制


* 当通过交换机一个端口的流量过大，超过了它的处理能力时，就会发生端口阻塞。流量控制的作用是防止在出现阻塞的情况下丢帧。
* 在半双工方式下，流量控制是通过反压（backpressure）技术实现的，模拟产生碰撞，使得信息源降低发送速度。
* 在全双工方式下流量控制一般遵循IEEE 802.3x标准。

#### 全双工流量控制


* IEEE802.3x标准定义了一种新方法，在全双工环境中去实现流量控制。交换机产生一个PAUSE帧，PAUSE帧使用一个保留的组播地址：01-80-C2-00-00-01，将它发送给正在发送的站，发送站接收到该帧后，就会暂停或停止发送。
* PAUSE帧利用了一个保留的组播地址，它不会被网桥和交换机所转发，这样，PAUSE帧不会产生附加信息量。

## MII接口介绍

MII接口提供了MAC和PHY之间、PHY与STA（Station Management）之间的互联技术，该接口支持10Mb/s与100Mb/s的数据传输速率，数据传输的位宽为4位。
MII通过增加数据位宽实现参考时钟的降低。
MII接口主要包括4个部分：


* 从MAC层到物理层的发送数据的接口
* 从物理层到MAC层的接受数据的接口
* 从物理层到MAC层的状态指示信号
* MAC层和物理层之间传送控制和状态信息的MDIO接口

MII接口可分为MAC模式和PHY模式，实际中主要用MAC模式，MAC模式的接口定义为：

{% img /imgage/embeded/MII.bmp %}
