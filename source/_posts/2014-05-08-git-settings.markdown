---
layout: post
title: "常用git设置"
date: 2014-05-08 20:52:50
comments: true
categories: Git
tags: git
---


## Git基本配置

	git config --global user.name 'dofa'
	git config --global user.email 'xxx@xxx.com'


## Git使用代理

	git config --global http.proxy http://127.0.0.1:8087
	git config --global https.proxy http://127.0.0.1:8087
	git config --global http.sslverify false

`http.sslverify`设置为`false`可以加快同步速度。

## Git显示漂亮日志

	git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative --show-signature"

## Git其它技巧

### 前一个分支

快速检出上一个分支：

	$ git checkout -
	# Switched to branch 'master'

	$ git checkout -
	# Switched to branch 'next'

	$ git checkout -
	# Switched to branch 'master'	

### `Stripspace`命令

`Git Stripspace`命令可以:

* 去掉行尾空白符
* 多个空行压缩成一行
* 必要时在文件末尾增加一个空行

使用此命令时必须传入一个文件，像这样：

	$ git stripspace < README.md	

### 提交空改动

可以使用`--allow-empty`选项强制创建一个没有任何改动的提交：

	$ git commit -m "Big-ass commit" --allow-empty

这样做在如下几种情况下是有意义的：

* 标记一批工作或一个新功能的开始。
* 记录你对项目进行了跟代码无关的改动。
* 跟使用你仓库的其他人交流。
* 作为仓库的第一次提交，因为第一次提交日后是不能被`rebase`的： `git commit -m "init repo" --allow-empty`.

### 更直观的Git Status

在命令行输入如下命令:

	$ git status -sb

### Git查询

`Git`查询运行你在之前的所有提交信息里进行搜索，找到其中和搜索条件相匹配的最近的一条。

	$ git show :/query

这里 `query` （区别大小写）是你想要搜索的词语， 这条命令会找到包含这个词语的最后那个提交并显示变动详情。

	$ git show :/typo

按 `q` 键退出命令。

### 合并分支

输入命令:

	$ git branch --merged

这会显示所有已经合并到你当前分支的分支列表。

相反地：

	$ git branch --no-merged

会显示所有还没有合并到你当前分支的分支列表。

### 使用网页查看本地仓库

使用`Git`的 `instaweb` 可以立即在 `gitweb`中浏览你的工作仓库。这个命令是个简单的脚步，配置了`gitweb`和用来浏览本地仓库的`Web`服务器。（译者注：默认需要`lighttpd`支持）

	$ git instaweb

### `Git`命令自定义别名

别名用来帮助你定义自己的`git`命令。比如你可以定义 `git a` 来运行 `git add --all`。

要添加一个别名， 一种方法是打开 `~/.gitconfig` 文件并添加如下内容：

	[alias]
	  co = checkout
	  cm = commit
	  p = push
	  # Show verbose output about tags, branches or remotes
	  tags = tag -l
	  branches = branch -a
	  remotes = remote -v

...或者在命令行里键入：

	$ git config --global alias.new_alias git_function

例如：

	$ git config --global alias.cm commit

指向多个命令的别名可以用引号来定义：

	$ git config --global alias.ac 'add -A . && commit'	

### 一些有用的别名：


别名 Alias | 命令 Command | 如何设置 What to Type |
--- | --- | --- 
`git cm` | `git commit` | `git config --global alias.cm commit` 
`git co` | `git checkout` | `git config --global alias.co checkout` 
`git ac` | `git add . -A` `git commit` | `git config --global alias.ac '!git add -A && git commit'` 
`git st` | `git status -sb` | `git config --global alias.st 'status -sb'` 
`git tags` | `git tag -l` | `git config --global alias.tags 'tag -l'` 
`git branches` | `git branch -a` | `git config --global alias.branches 'branch -a'` 
`git remotes` | `git remote -v` | `git config --global alias.remotes 'remote -v'` 
`git lg` | `git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --` | `git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"` 

### 自动更正

	$ git config --global help.autocorrect 1

### 带颜色输出

	$ git config --global color.ui 1
