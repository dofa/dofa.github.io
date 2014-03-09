---
layout: post
title: "Vagrant使用简介"
date: 2014-03-09 06:21:16 +0000
comments: true
categories: VM
tags: vm, vagrant, virtualbox
---


## Vagrant简介

> Vagrant is a tool for building complete development environments. With an easy-to-use workflow and focus on automation, Vagrant lowers development environment setup time, increases development/production parity, and makes the "works on my machine" excuse a relic of the past.



## Vagrant安装

#### virtualbox

https://www.virtualbox.org

#### vagrant

http://www.vagrantup.com

#### box

http://www.vagrantbox.es

## Vagrant使用

#### 使用下载的box初始化

	vagrant box add precise32 http://files.vagrantup.com/precise32.box

#### 初始化开发环境

	cd ~/dev	#开发目录
	vagrant init precise32
	

#### 运行Vagrant box

	vagrant up

#### 远程连接到box

	vagrant ssh


#### 其他常用Vagrant命令

	vagrant box add NAME URL			#添加一个box
	vagrant box list					#查看本地已添加的box
	vagrant box remove NAME virtualbox	#删除本地已添加的box，如若是版本1.0.x，执行$ vagrant box remove  NAME
	vagrant init NAME					#初始化，实质应是创建Vagrantfile文件         
	vagrant up							#启动虚拟机
	vagrant halt						#关闭虚拟机
	vagrant destroy						#销毁虚拟机
	vagrant reload						#重启虚拟机
	vagrant package						#当前正在运行的VirtualBox虚拟环境打包成一个可重复使用的box            
	vagrant ssh							#进入虚拟环境

## Vagrant高级 

#### Vagrant配置文件Vagrantfile

官方解释是这样的：The primary function of the Vagrantfile is to describe the type of machine required for a project, and how to configure and provision these machines。翻译出来太生涩，简单来说就是配置这个虚拟主机网络连接方式，端口转发，同步文件夹，以及怎么和puppet，chef结合的一个配置文件。执行完`vagrant init`后,在工作目录中,你会发现此文件。


使用V2版本配置：

{% raw %}
```ruby
Vagrant.configure("2") do |config|
	# ...
end
```
{% endraw %}

#### 配置网络

* 端口转发：（假设虚拟机的80端口提供web服务，此处将通过访问物理机的8080端口转发到虚拟机的80端口，来实现web的访问）

{% raw %}
```ruby
Vagrant.configure("2") do |config|
	config.vm.network :forwarded_port, guest: 80, host: 8080
end
```
{% endraw %}

* 桥接网络（公共网络，局域网DHCP服务器自动分配IP）

{% raw %}
```ruby
Vagrant.configure("2") do |config|
	config.vm.network :public_network
end
```
{% endraw %}

	VBoxManage list bridgedifs | grep ^Name    #可通过此命令查看本机的网卡

* 私有网络：允许多个虚拟机通过主机通过网络互相通信，vagrant允许用户分配一个静态IP，然后使用私有网络设置。

{% raw %}
```ruby
Vagrant.configure("2") do |config|
	config.vm.network :private_network, ip: "192.168.50.4"
end
```
{% endraw %}

#### 同步文件夹

默认的，vagrant将共享你的工作目录（即Vagrantfile所在的目录）到虚拟机中的/vagrant,所以一般不需配置即可，如你需要可配置：

{% raw %}
```ruby
Vagrant.configure("2") do |config|
	# other config here
	config.vm.synced_folder "src/", "/srv/website"
end
```
{% endraw %}

"src/"：物理机目录;"/srv/website"虚拟机目录

