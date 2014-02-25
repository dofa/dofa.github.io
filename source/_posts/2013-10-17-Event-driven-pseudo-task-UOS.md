---
layout: post
title: 事件驱动的伪任务-UOS
category: Embedded
tags: Embedded Uos Task Protothread
description: 基于protothread原理事件驱动的伪任务 UOS
---

### protothread
protothread是专为资源有限的系统设计的一种耗费资源特别少并且不使用堆栈的线程模型

### 相比于嵌入式操作系统， protothread其有如下优点：

+ 以纯C语言实现，无硬件依靠性； 因此不存在移植的困难
+ 极少的资源需求，每个 Protothread 仅需要2个额外的字节
+ 支持阻塞操纵且没有栈的切换

### protothread的缺陷在于：

+ 函数中不具备可重入型，不能使用局部变量；
+ 按顺序判断各任务条件是否满足，因此无优先级抢占；
+ 任务中的各条件也是按顺序判断的，因此要求任务中的条件必须是依次出现的。

### Uos的核心便是protothread

+ Uos使用protothread实现Task Switch
+ Uos另外一个先进的地方：event-driven

### Uos的Task Switch和event-driven

+ Task Switch负责把任务所有权切换出去
+ 切换任务之前，要设置触发事件
+ 任务调度时，会根据是否有触发事件发生，调用该任务

### UOS项目官网

+ project网址：http://www.uos.co
+ github网址：https://github.com/bitbegin/uos