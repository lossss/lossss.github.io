---
title: node-notes
date: 2017-11-18 15:41:34
categories: node
tags: node
---

<!--more-->
##node 安装

1.使用nvm控制版本
nvm安装 [参考](https://github.com/creationix/nvm)
```bash
#查看当前已安装的版本
nvm ls
# 查看远端版本
nvm ls-remote
# 安装node
# nvm install node
nvm install v8.9.4
# 切换node版本
# nvm use node
nvm use v8.9.1
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