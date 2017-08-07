---
title: atom proxy
date: 2017-08-05 22:06:17
tags: atom
categories: tools
---
atom 中配置路由
<!--more-->


今天尝试了一下使用atom 感觉和sublime很像 主要是看上了她的markdown实时的编辑
但是atom下载packages的时候连的外网却连不上 我这边开了本地的1080端口开了代理所以进行如下操作即可

cmd 运行：

```bash
apm config set strict-ssl false
apm config set https-proxy http://127.0.0.1:1080
```
参考文章

Atom代理设置 http://www.jianshu.com/p/24cd35cd4b03
