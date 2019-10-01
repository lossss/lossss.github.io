---
title: node-notes
date: 2017-11-18 15:41:34
categories: node
tags: node
---

<!--more-->
##node 安装

```bash
#先更新系统
sudo apt install update
sudo apt install upgrade

sudo apt install node
```
1. npm
```bash
sudo apt install npm
# npm  升级 (先升级node版本再升级npm)
npm install npm@latest -g
```
国内可以使用 [cnpm](http://npm.taobao.org/)

1. node 版本管理
```bash
sudo npm install -g n
//安装官方最新版本
sudo n latest
//安装官方稳定版本
sudo n stable
//安装官方最新LTS版本
sudo n lts
```