---
title: javaweb
date: 2019-02-25 11:33:35
categories:
tags:
---
基于idea,复习javaweb的基础知识
<!--more-->

## 工具

### chrome

#### 使用chrome 查看请求头和请求体

F12控制台然后照下图选择即可
![1.png](https://losssblog.oss-cn-hangzhou.aliyuncs.com/javaweb/1.png)

## JavaEE

### IEDA关联tomcat

Intellij IDEA->Preferences
![javaweb-2.jpg](https://losssblog.oss-cn-hangzhou.aliyuncs.com/javaweb-2.jpg)

新建web动态工程
![javaweb-3.jpg](https://losssblog.oss-cn-hangzhou.aliyuncs.com/javaweb-3.jpg)
![javaweb-4.jpg](https://losssblog.oss-cn-hangzhou.aliyuncs.com/javaweb-4.jpg)

### tomcat 目录说明












## 问题集

### jdbc

1. `java.sql.SQLException: Can not call getNString() when field's charset isn't UTF-8`

使用getString() 替代 getNString()
