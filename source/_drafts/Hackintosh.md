---
title: Hackintosh
date: 2017-12-03 18:30:52
categories:
tags:
---

<!--more-->

## 文档
[start](https://www.tonymacx86.com/threads/faq-read-first-laptop-frequent-questions.164990/)
[clover wiki](https://clover-wiki.zetam.org/zh-CN/contents)
> 中文 业界良心
[tonymacx86](https://www.tonymacx86.com/threads/unibeast-install-macos-high-sierra-on-any-supported-intel-based-pc.235474/)
[远景](http://bbs.pcbeta.com/forum-498-1.html)
[黑苹果乐园](https://imac.hk/install-os-x-mbt-gpt-uefi.html)
[资源](http://bbs.pcbeta.com/viewthread-1737566-1-1.html)

## vmware mac os install

## osx 挂载硬盘
```bash
diskutil list

diskutil mount disk1s1
```

## win 挂载硬盘
```bash
diskpart

list disk

sel disk 3

list part

sel part 1

assign
```
> 需要一个虚拟环境 便于操作
[安装参考](https://jingyan.baidu.com/article/54b6b9c0ec0a1b2d593b4745.html)

## 问题集

### [Window Server Service only ran for 0 seconds](https://www.tonymacx86.com/threads/fix-window-server-service-only-ran-for-0-seconds-with-dual-gpu.233092/) 

> [iasl](https://github.com/RehabMan/Intel-iasl)

### Operation not permitted
You need to press Cmd + R at boot time, open the terminal and then run csrutil disable and reboot

### win时间和mac时间不同
win下管理员cmd
```
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
```

## 微星ge60安装osx 10.13
### usb启动制作部分
1. 虚拟机安装osx(使用mac电脑制作最好)
2. appstore 下载high sierra 如果直接用createinstallmedia安装的话会有以下错误
Applications Install macOS High Sierra.app does not appear to be a valid OS installer application.
3. 双击下载的macos high sierra 开始安装 等到重启时不要重启
打开 /macOS Install Data(根目录下) 复制里面所有内容 '/Applications/Install macOS High Sierra.app/Contents/SharedSupport'(SharedSupport不存在的话新建)
4. 执行以下指令 等待完成
```bash
sudo /Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```
5. 安装clover