---
layout: post
title: "使用oh my zsh替代bash"
date: 2014-04-24 21:30:50
comments: true
categories: Shell
tags: bash, zsh
---


## 安装zsh

	apt-get install zsh

## 安装OH-My-ZSH

#### 手动安装

	cd ~
	git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh

	cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc


设定为默认bash

	chsh -s /bin/zsh

#### 自动安装

via `curl`

	curl -L http://install.ohmyz.sh | sh

via `wget`

	wget --no-check-certificate http://install.ohmyz.sh -O - | sh

## 修改putty不能显示的字符

`~/.oh-my-zsh/themes/robbyrussell.zsh-theme`

	#PROMPT='%{$fg_bold[red]%}➜ %{$fg_bold[green]%}%p %{$fg[cyan]%}%c %{$fg_bold[blue]%}$(git_prompt_info)%{$fg_bold[blue]%} % %{$reset_color%}'
	PROMPT='%{$fg_bold[red]%}# %{$fg_bold[green]%}%p %{$fg[cyan]%}%c %{$fg_bold[blue]%}$(git_prompt_info)%{$fg_bold[blue]%} % %{$reset_color%}'
	ZSH_THEME_GIT_PROMPT_PREFIX="git:(%{$fg[red]%}"
	ZSH_THEME_GIT_PROMPT_SUFFIX="%{$reset_color%}"
	#ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[blue]%}) %{$fg[yellow]%}✗%{$reset_color%}"
	ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[blue]%}) %{$fg[yellow]%}X %{$reset_color%}"
	ZSH_THEME_GIT_PROMPT_CLEAN="%{$fg[blue]%})"

使用更改后的配置：

	source `~/.oh-my-zsh/themes/robbyrussell.zsh-theme`

## 	OH-My-ZSH的使用

* 强大的历史纪录功能，输入 grep 然后用上下箭头可以翻阅你执行的所有 grep 命令。
* 智能拼写纠正，输入gtep mactalk * -R，系统会提示：zsh: correct ‘gtep’ to ‘grep’ [nyae]? 比妹纸贴心吧，她们向来都是让你猜的……
* 各种补全：路径补全、命令补全，命令参数补全，插件内容补全等等。触发补全只需要按一下或两下 tab 键，补全项可以使用 ctrl+n/p/f/b上下左右切换。比如你想杀掉 java 的进程，只需要输入 kill java + tab键，如果只有一个 java 进程，zsh 会自动替换为进程的 pid，如果有多个则会出现选择项供你选择。ssh + 空格 + 两个tab键，zsh会列出所有访问过的主机和用户名进行补全
* 目录浏览和跳转：输入 d，即可列出你在这个会话里访问的目录列表，输入列表前的序号，即可直接跳转。
* 在当前目录下输入 .. 或 … ，或直接输入当前目录名都可以跳转，你甚至不再需要输入 cd 命令了。
* 通配符搜索：ls -l **/*.sh，可以递归显示当前目录下的 shell 文件，文件少时可以代替 find，文件太多就歇菜了。
