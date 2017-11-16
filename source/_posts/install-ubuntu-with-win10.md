---
title: install-ubuntu-with-win10
date: 2017-11-15 08:40:20
categories: ubuntu
tags:
---
使用ubuntu和win10双系统
<!--more-->
## why ubuntu
1. 没钱买mac
2. win下的命令行还是太弱了

## let's go

1. [ubuntu](https://www.ubuntu.com/download/desktop) 

2. [unetbootin](https://unetbootin.github.io/)

3. 插入u盘 按如下设置
![setting](http://ou7k0sem6.bkt.clouddn.com/blog/171115/l0hh4KHd3A.png?imageslim)

4. 重启电脑然后选择从u盘启动

## 换源

```bash
# 备份一下
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
# 修改
sudo vi /etc/apt/sources.list

```
替换为以下
```bash
deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
```