---
layout: post
title: "Sublime Text 学习笔记"
date: 2013-06-01 16:25:52 +0000
comments: true
tags: sublime-text
categories: SublimeText
---

* 如果你的配置错误，导致Sublime Text2不能打开了，想要把配置改回来，那么配置文件在C:\Users\用户名\AppData\Roaming\Sublime Text 2\Packages\User中
* 安装Package control，按快捷键Ctrl+`，打开命令输入界面（一般在下方），输入下面的命令后回车即可，重启Sublime Text2

```python
import urllib2,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())
```
* 修改字体
Preferences->File Setting-User，打开配置文件，看里面有没font_face配置项，有就直接改，没有就自己加上，可能的配置文件如下：
```
{
    "color_scheme": "Packages/Color Scheme - Default/Black-Pearl2.tmTheme",
    "font_face": "微软雅黑",
    "font_size": 10.0
}
```
* 设置代理(GoAgent)
打开`settings - user`，输入：
```
	"http_proxy": "http://127.0.0.1:8087",
	"https_proxy": "http://127.0.0.1:8087"
```
* 同时编辑多行 (Ctrl+Shift+L (Win) 或  Command+Shift+L (Mac))
如要在选中的多行文本的最后面同时添加一个字符“a”，先选中要编辑的多行文字，然后按快捷键，此时每行的末尾都会有个输入光标在闪，再按End键将鼠标定位到行末，（再按Home键将鼠标定位到行首）输入字母a即可。如要退出多行编辑状态，按Esc键即可。

* 一次性选择全部的相同文本 (Alt+F3 (Win) 或 Ctrl+Command+G (Mac))

* 竖向多行选择 (Shift+鼠标右键 (Win) 或 Option+鼠标左键 (Mac))

* 手动选择多处不同文本 (Ctrl+鼠标左键(Win) 或 Command+鼠标左键(Mac) )


