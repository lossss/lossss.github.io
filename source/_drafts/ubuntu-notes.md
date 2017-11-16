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
## 安装&卸载软件

### .deb

```bash
sudo dpkg -i XXX.deb # XXX为该deb包的文件名
#如果出现错误则安装依赖
apt-get install -f
```

自动清除残留配置文件
```bash
sudo apt-get autoclean 
sudo apt-get autoremove
```

完全卸载
```bash
sudo apt-get remove --purge name
```
解压tar.gz文件
```bash
tar -xzvf file.tar.gz
```
参考 https://zhuanlan.zhihu.com/p/27187622
