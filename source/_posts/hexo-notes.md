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

2. ~~push 上去的themes中的next文件夹是空的这个暂时没想好怎么解决~~直接删除next的.git文件即可 如果不行可以用`git rm --cached themes/next`清除缓存试试

3. 部署后css不加载
  - 1. 在_config.yml 中修改url为新的url
  - 2. 删除.deploy_git
  - 3. hexo d -g

## 写blog时的图片处理

### 图片压缩

当然你可以使用 [tinypng](https://tinypng.com/)来压缩你的图片文件
我用的是 命令行版本 https://www.npmjs.com/package/tinypng-cli
1. 安装

`npm install -g tinypng-cli`

你需要在官网申请一个api key 然后在自己的home路径下新建一个.tinypng文件吧自己的key放进去

2. 使用

- 压缩当前目录下所有图片：tinypng .
递归压缩子目录：tinypng -r
- 压缩当前目录下所有图片：tinypng .
- 递归压缩子目录：tinypng -r
- 压缩单个目录：tinypng assets/img
- 压缩多个目录：tinypng assets/img1 assets/img2
- 压缩单张图片：tinypng assets/img/demo.png
- 压缩多张图片：tinypng assets/img/demo1.png assets/img/demo2.png
- 单独指定API key：tinypng demo.png -k E99a18c4f8cb3EL5f2l08u368_922e03

### 图床工具

现在使用的是 [PicGo](https://picgo.github.io/PicGo-Doc/zh/)

vscode 上有对应的插件 因为我这里用的是阿里OSS 如果要使用这个插件的话需要再OSS后台设置 `图片处理->访问设置->原图保护(关闭)` 当然对应的防盗链也是可以直接开启的不影响

vscode 上快捷键为`cmd+opt+u` 可以直接复制文件之后直接按快捷键复制到vscode 中,免去了复杂的上传操作

还有需要注意的是 图片的名字不能有空格 不然链接名字会不准确

我的blog的编辑流如下
`写blog->截图修改名字(例:hexo-notes-1.jpg)->图片压缩网压缩->vs-picgo->实时markdown预览(shift+opt+m)`
