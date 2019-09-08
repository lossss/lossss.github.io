---
title: nas-ubuntu
date: 2019-09-08 14:03:21
categories: nas
tags: [nas,ubuntu]
---
在群晖nas上安装ubuntu
<!--more-->
最终效果 使用群晖自带的dnns实现外网ssh访问

## 安装ubuntu

1. 下载ubuntu镜像

2. 在群晖套件中心下载群晖VMM

3. VMM设置

- 下载 Guest Tool
![nas-ubuntu-1.png](https://losssblog.oss-cn-hangzhou.aliyuncs.com/nas-ubuntu-1.png)
- 新增->选择自己刚刚下载的ubuntu镜像
- 完成后状态如下图
![nas-ubuntu-2.png](https://losssblog.oss-cn-hangzhou.aliyuncs.com/nas-ubuntu-2.png)

- 虚拟机->新增这里都比较简单 按自己需要设置就行需要注意的是其他设置里面选择启动iso文件是用的ubuntu的镜像文件,下面一个选择刚刚的Guest Tool
如果这里有什么不明白可以参考[群晖的官方视频教程](https://www.bilibili.com/video/av25745315/)

4. 测试ssh

`ssh 用户名@内网地址`

## 外网设置

需要自己家网有外网ip 这部分可以参考 [视频](https://www.youtube.com/watch?v=6baVu1yLZ9Q)

1. 需要在路由器设置端口转发

1. 设置群晖的DNNS

1. 配置好后可以使用 ssh -p 22 用户名@主机域名 就可以直接连到我们在nas上的ubuntu主机了