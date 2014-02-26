---
layout: post
title: "Sublime Text 入门及技巧"
date: 2013-06-01 14:25:52 +0000
comments: true
tags: sublime-text
categories: SublimeText
---

## 快捷的命令面板
和 TextMate 类似，Sublime Text 2 也提供了很方便的命令调用方式：Command Palette（命令面板）。调用方法：直接在 `Tool` 菜单中选择 `Command Palette`，或是用快捷键：`Shift+Command+P`，输入命令名称（中的字母）就可以实时搜索到相应的命令、选项、snippet 和 syntex， 按下回车就可以直接执行，减少了查找的麻烦。

## 即时的文件切换
按下 `Command+P`(Mac) 或是 `Ctrl+P`(Windows)，输入想要切换到的文件的文件名，都不用按下回车键，目标文件就已经展现在眼前了，虽然 Vim 配合 PeepOpen 也可以实现同样的功能，但速度却远没有这么迅速。

## 随心所欲的跳转
`Cmd+P` 之所以被叫做 Goto Anything 并不是虚名：

* 用 `Command+P` 可以快速跳转到当前项目中的任意文件，可进行关键词匹配。
* 用 `Command+P` 后 `@` (或是`Command+R`)可以快速列出/跳转到某个函数（很爽的是在 markdown 当中是匹配到标题，而且还是带缩进的！）。
* 用 `Command+P` 后 `#` 可以在当前文件中进行搜索。
* 用 `Command+P` 后 `:` (或是`Ctrl+G`)加上数字可以跳转到相应的行。

而更酷的是你可以用 `Command+P` 加上一些关键词跳转到某个文件同时加上 `@` 来列出/跳转到目标文件中的某个函数，或是同时加上 `#` 来在目标文件中进行搜索，或是同时加上 `:` 和数字来跳转到目标文件中相应的行。

## 多重选择(Multi-Selection)
多重选择功能允许在页面中同时存在多个光标，让很多本来需要正则表达式、高级搜索和替换才能完成的任务也变得游刃有余了。
激活多重选择的方法有两几种：

* 按住 `Command` 或 `Alt`，然后在页面中希望中现光标的位置点击。
* 选择数行文本，然后按下 `Shift+Command+L`。
* 通过反复按下 `Control/Command+D` 即可将全文中与光标当前所在位置的词相同的词逐一加入选择，而直接按下 `Alt+F3`(Windows) 或是 `Ctrl+Command+G`(Mac) 即可一次性选择所有相同的词。
* 按下鼠标中键来进行垂直方向的纵列选择，也可以进入多重编辑状态。


