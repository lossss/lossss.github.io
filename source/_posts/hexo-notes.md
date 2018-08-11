---
title: hexo-notes
date: 2017-11-26 13:22:42
categories: hexo
tags: hexo
---
hexo博客搭建笔记
<!--more-->

## [博客源码](https://github.com/lossss/lossss.github.io) branch:dev

## 安装过程
```bash
brew install node
//换源
npm config set registry https://registry.npm.taobao.org
//install hexo
npm install -g hexo
//init
cd blog
npm install
hexo clean
hexo g
hexo s
hexo d -g
```

## 本博客编译问题
1. 确保更新到最新的node和hexo

2. push 上去的themes中的next文件夹是空的这个暂时没想好怎么解决

3. 部署后css不加载
  1. 在_config.yml 中修改url为新的url
  2. 删除.deploy_git
  3. hexo d -g

## 使用[qshell](https://developer.qiniu.com/kodo/tools/1302/qshell)上传图片

## 图片命名规范
统一命名方便管理 博客名-01.png 例: 12win-01.png

## [图片压缩](http://upng.photopea.com/)