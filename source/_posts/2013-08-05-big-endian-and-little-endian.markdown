---
layout: post
title: big endian与little endian（大小端） 
date: 2013-08-05 13:25:52 +0000
comments: true
tags: Embeded 
categories: Embedded
---

在C编程中，经常遇到大小端（big endian与little endian）的问题，尤其涉及到位域的情况，很容易出错。我这里总结下C51和HTCC C18两种compiler对大小端的处理。

## Check Endian code 

```c
char checkEndian(void)
{
	union check{
		unsigned int a;
		unsigned char b;
	};
	union check ck;
	ck.a = 1;
	return (ck.b==1) ;
}

void main(void)
{
	union uE{
		unsigned long num;
		struct{
			unsigned char a1:1;
			unsigned char b3:3;
			unsigned short c16;
			unsigned char d3:3;
			unsigned char e1:1;
		}sN;
	};

	union uE a;
	char ttt = 	checkEndian();

	a.num = 0x12345678;
	a.num = 0;

	a.sN.a1 = 1;
	a.sN.b3 = 2;
	a.sN.c16 = 0x0304;
	a.sN.d3 = 5;
	a.sN.e1 = 1;

	a.num;

}
```

## Executed results

a.num = ?

对于big endian：

以C51来分析，结构成员按照定义顺序从小地址到大地址存放到ram中，显然按照地址从小到大排放结果就为：

```c
05 03 04 0d
```

转换为大端显示为：

```c
0x0503040d
```

对于little endian：

结果为

```c
0x0d030405
```

## Results

所以我这里结论：

* 位域没有大小端的区别，区别在于各编译器的实现。上面的例子便是没有区别的compiler，C51和HTCC C18；网络字节序位域有大小端区别，这个一定要注意

* 两个及其以上字节有大小端区别
