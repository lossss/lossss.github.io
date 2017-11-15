---
title: ubuntu-notes
date: 2017-11-15 08:36:45
categories:
tags:
---

<!--more-->

## ubuntu 中安装软件的方法
1. apt
```bash
1. 普通安装：apt-get install softname1 softname2 …;
2. 修复安装：apt-get -f install softname1 softname2... ;
(-f Atemp to correct broken dependencies)
3. 重新安装：apt-get --reinstall install softname1 softname2...;
```

[清理](https://linux.cn/article-5069-1.html)