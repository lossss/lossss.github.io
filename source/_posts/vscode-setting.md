---
title: vscode-setting
date: 2017-09-28 15:07:58
categories: tools
tags: vscode
---
vscode 设置
<!--more-->

## 常用设置

1. 隐藏菜单栏

ctrl+shift+p

view：toggle menu bar

想使用的时候按alt

2. 修改字体

在文件 首选项 设置 用户设置中加入`"editor.fontSize":17`即可

## 常用快捷键
| 快捷键       | 功能                                                   |
| ------------ | ------------------------------------------------------ |
| ctrl+shift+p |                                                        |
| ctrl+shift+n | 因为不能同时打开多个项目所以只能新建窗口来打开新的项目 |
| shift+alt+f  | 格式化文件                                             |
| ctrl+p       | 打开文件                                                       |


## 常用插件

> 按下ctrl+shift+p 后输入 ext回车 或者点击左侧第五个图标 就可以搜索自己需要的插件了

### 通用

1. vscode-icons

2. output colorizer

3. guides
> 代码对齐辅助线

4. ~~没有找到 文件显示git status状态的插件(类似atom的tree-view-git-status)~~ 最新版本已经自带此功能

5. Settings Sync
> 同步设置

6. Search Docsets
> 查看文档  需要提前安装 velocity 快捷键 shift+F1 mac中对应的插件为dash

### vim

1. vim

2. relative-line-numbers

### python

1. python

2. magicpython
> python文件着色器

### markdown

1.  vscode markdown preview enhanced
安装好后 ctrl+shift+m 预览 或者也可以用vs自带的ctrl+k v 打开预览

## debug

### python

安装python插件之后 按f5 就可以进行调试
当需要使用input 或者需要输出图片的时候 在左上选择integrated terminal/console 在运行即可
