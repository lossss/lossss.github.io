---
title: mac-notes
date: 2017-11-03 15:35:24
categories: tools
tags: mac
---
mac 备忘
<!--more-->

## 常用软件

### 系统相关

1. cleanmymac

1. [The Unarchiver](https://theunarchiver.com)
 解压软件

1. [paragon ntfs](https://china.paragon-software.com/home-mac/ntfs-for-mac/)

1. [mac fan control](https://www.crystalidea.com/macs-fan-control)

## 效率

1. [moom](https://manytricks.com/moom/)
高效的分屏软件

1. [spacelaucherapp](https://spacelauncherapp.com)

### 学习相关

1. [marginnote](https://marginnote.com/?lang=zh-hans)

2. [voodoopad](https://www.primatelabs.com/)

3. [mindnode](https://mindnode.com/)

>思维导图 没钱可以用xmind

### design

1. [sketch](https://www.sketchapp.com/)

> sketch+Sketch Measure

## 常用设置

### 打开任何来源

```bash
sudo spctl --master-disable
```

### [homebrew](https://brew.sh/)

### iterm2 proxy

```bash
export http_proxy=http://127.0.0.1:1080
export https_proxy=$http_proxy
```

如需自动切换
可以在 ~/.zshrc 或者 ~/.bash_profile 中添加这样的alias：

```bash
alias goproxy='export http_proxy=http://127.0.0.1:8087 https_proxy=http://127.0.0.1:8087'
alias disproxy='unset http_proxy https_proxy'
```

测试是否切换成功 看下ip的归属地

```bash
curl ifconfig.me
```

### 按键区别

| mac             | windows   |
|:----------------|:----------|
| ⌘——Command ()  | win       |
| ⌃ ——Control     | ctrl      |
| ⌥——Option (alt) | alt       |
| ⇧——Shift        | shift     |
| ⇪——Caps Lock    | Caps Lock |

### 快捷键

1 cmd+空格 cmd+b 在浏览器中搜索

个人习惯把大写键改为command键
keyboard -> modifier keys -> usb keyboard -> Caps Lockey 改为command

2 程序切换

- 2.1 程序内部切换 command+~

- 2.2 程序间切换 command+tab

3 显示隐藏文件
command + Shift + .

4 拷贝finder 路径
command+option+c

### 常用小技巧

1 创建快捷方式
option+command 鼠标拖动

2 其实mac上还有很多实用的小功能 可以参看以下这个[视频](https://www.bilibili.com/video/av23430954)
