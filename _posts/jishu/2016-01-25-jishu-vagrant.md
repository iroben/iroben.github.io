---
layout: post
title: vagrant搭建laravel开发环境
category: 技术
---

今年因为学习`laravel `了解到了`vagrant`，可以用`vagrant`和`virtualbox`搭建开发环境，这种方式非常好

1. 在团队开发开发的时候，可以统一开发环境，不要在开发环境上浪费太多时间
2. 开发环境管理方便，以前我一直在PHP5.3上开发，现在因为到用到一些PHP的新特性，不得不升级到5.6，但有的时候又想用PHP5.3，说的比较极端，不排除没有这种情况，这种情况下，如果在自己机器上整，非常折腾，如果用虚拟机的话就非常方便，一个PHP5.3的虚拟机，一个PHP5.6的虚拟机
3. 程序代码和运行环境分开，可以在不更改代码的情况下切换环境

搭建开发环境，我们先要下载安装 [virtualbox](https://www.virtualbox.org/)  [vagrant](https://www.vagrantup.com/) 

`git clone https://github.com/laravel/homestead.git Homestead`

进入homestead目录，执行`bash init.sh`命令

## 配置共享目录
打开`~/.homestead/Homestead.yaml`，修改`folders`的`map`和`to`，`map`是指你电脑要共享到虚拟机的目录，`to`是`map`目录要映射到虚拟机的目录

```yaml
folders:	
    - map: ~/www 
      to: /home/vagrant/www
    
```
启动虚拟机`vagrant up`，第一次要在线下载虚拟机镜像，比较慢，你也可以先把镜像下载下来，再添加虚拟机

```shell
vagrant box add homestead/laravel /path/xxx/virtualbox.box
vagrant up
```
启动完成后执行`vagrant ssh`用shell连接Linux虚拟机，接下来就可以在虚拟机做你该做的事了

`vagrant`常用命令

```shell
vagrant init		初始化vagrant file
vagrant up		启动虚拟机
vagrant halt		关机
vagrant package	打包
vagrant reload	重新启动
vagrant box list	虚拟机列表
vagrant box add virtualname /path/xx/virtualbox.box
vagrant box remove virtualname
vagrant destroy
```