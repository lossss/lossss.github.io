---
title: install-ubuntu-with-win10
date: 2017-11-15 08:40:20
categories:
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
我选择的是 install ubuntu alongside windows

## 一些功能

### 安装搜狗输入法

[安装步骤参考](http://blog.topspeedsnail.com/archives/6955)

如果出现两个搜狗输入法图标的时候执行

```bash
sudo apt-get remove fcitx-ui-qimpanel
```
如果搜狗提示为乱码 看看字库没有安装，没有在Languages里面把中文选进去
### 装chrome

[步骤参考](http://www.linuxidc.com/Linux/2016-05/131096.htm)

### 安装上网
[参考](https://github.com/shadowsocks/shadowsocks-libev)

### 视频播放软件

### 启动栏：Docky

### 美化/主题：Unity Tweak Tool

### 网易云音乐