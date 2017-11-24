---
title: install-ubuntu-with-win10
date: 2017-11-15 08:40:20
categories: ubuntu
tags:
---
使用ubuntu和win10双系统
<!--more-->
## why ubuntu
1. 没钱买mac
2. win下的命令行还是太弱了

## let's go

1. [ubuntu](https://www.ubuntu.com/download/desktop)

2. [unetbootin](https://unetbootin.github.io/)

3. 插入u盘 按如下设置
![setting](http://ou7k0sem6.bkt.clouddn.com/install-ubuntu-with-win10/1.png)

4. 重启电脑然后选择从u盘启动
我选择的是 install ubuntu alongside windows

## 一些设置
[开机默认启动windows](https://jingyan.baidu.com/article/63acb44ae4062c61fcc17e27.html)

## 常用软件

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

使用dpkg卸载
```bash
sudo dpkg -r packagename # 如果不知道packagename 可以用 sudo dpkg -i xxx.deb 查询
```

解压tar.gz文件
```bash
tar -xzvf file.tar.gz
```
参考 https://zhuanlan.zhihu.com/p/27187622

解压zip
```bash
sudo apt install unar
unar your-zip
```
更多命令行的内容可以参考我的另一篇博客{% post_link linux-notes %}

### 安装搜狗输入法

[安装步骤参考](http://blog.topspeedsnail.com/archives/6955)

### 装chrome

[步骤参考](http://www.linuxidc.com/Linux/2016-05/131096.htm)

### 必要组件
[参考](https://github.com/shadowsocks/shadowsocks-libev)
[开机启动参考](https://blog.huihut.com/2017/08/25/LinuxInstallConfigShadowsocksClient/)
开机设置路径备份 /etc/systemd/system/shadowsocks.service

### 视频播放软件 [vlc](http://www.videolan.org/vlc/download-ubuntu.html)

### 截图 shutter
```bash
sudo apt install shutter
```

### albert
```bash
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt update
sudo apt install albert

# 设置开机自动启动
ln -s /usr/share/applications/albert.desktop ~/.config/autostart/
```

### 美化/主题：Unity Tweak Tool

### 网易云音乐
官网下载.deb即可 
如果用命令装的时候不行的话记得换源

### [terminator](https://gnometerminator.blogspot.hk/p/introduction.html)
常用快捷键 [官方文档](http://terminator-gtk3.readthedocs.io/en/latest/gettingstarted.html)
* 上下分屏=>c+s+o,左右分屏=>c+s+e
* 关闭一个窗口或分屏=>c+s+w,退出终端=>c+s+q
* 控制窗口大小 快捷式：c+s+ ←↑↓→,切换窗口c+tab 窗口最大化=> F11
* Move to the terminal above the current one: Alt + ↑
* Move to the terminal below the current one: Alt + ↓
* Move to the terminal left of the current one: Alt + ←
* Move to the terminal right of the current one: Alt + →

自定义打开时的位置和大小
1. 打开terminator 调节好大小后输入
```bash
xwininfo
```
2. 选择当前窗口后 复制最后一行 -geometry 891x528+395+319

3. 打开`system settings->keyboard->shortcuts->custom shortcuts-> +`
command中加入
```bash
terminator --geometry 891x528+395+319
```
4. 点击disable 设置快捷键 ctrl+alt+t

### [zeal](https://zealdocs.org/) 

### [vscode](https://code.visualstudio.com/)

### [Jetbrains](https://www.jetbrains.com/)
```bash
tar xxx.tar.gz
cd xxx
sudo chmod a=+rx bin/idea.sh
sudo bin/idea.sh
```
### [vscode](https://code.visualstudio.com/)
```安装更新
sudo apt install ~/path/to/code_1.XXX.deb
```

### [java](http://tipsonubuntu.com/2016/07/31/install-oracle-java-8-9-ubuntu-16-04-linux-mint-18/)
```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt update; sudo apt install oracle-java8-installer  # You may replace oracle-java8-installer with oracle-java9-installer to install Java 9. 
java -version #check version
sudo apt install oracle-java8-set-default # For Java 9, install the package oracle-java9-set-default instead
```
## 换源

```bash
# 备份一下
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
# 修改
sudo vi /etc/apt/sources.list

```
替换为以下
```bash
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb http://mirrors.aliyun.com/ubuntu/ xenial multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse #Added by software-properties
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-security multiverse

```
## 安装字体
Monaco
```bash
#!/bin/bash

#script extraido de: http://paulocassiano.wordpress.com/2008/08/29/deixando-o-gedit-com-a-cara-do-textmate/
#tip for better "resolution" here: http://blog.siverti.com.br/2008/05/22/fonte-monaco-no-ubuntugedit/

cd /usr/share/fonts/truetype/

#TODO: put validation if folder already exists
sudo mkdir ttf-monaco

cd ttf-monaco/

sudo wget http://www.gringod.com/wp-upload/software/Fonts/Monaco_Linux.ttf

#create an index of X font files in a directory
sudo mkfontdir

#go to parent folder /usr/share/fonts/truetype
cd ..

fc-cache
```
## 使用简体中文
方法一：可以修改系统文字为中文

方法二：既要使用英文作为系统字体 又要显示简体汉字
[参考](https://memo.ink/fix-chinese-font-display-under-en-environment/)

简单来说就是修改/etc/fonts/conf.avail/64-language-selector-prefer.conf
```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Noto Sans CJK JP</family>
			<family>Noto Sans CJK SC</family>
			<family>Noto Sans CJK TC</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Noto Sans Mono CJK JP</family>
				<family>Noto Sans Mono CJK SC</family>
			<family>Noto Sans Mono CJK TC</family>
		</prefer>
	</alias>
</fontconfig>
```
改为以下即可
```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Noto Sans Mono CJK SC</family>
			<family>Noto Sans Mono CJK TC</family>
<family>Noto Sans Mono CJK JP</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Noto Sans Mono CJK SC</family>
			<family>Noto Sans Mono CJK TC</family>
			<family>Noto Sans Mono CJK JP</family>
		</prefer>
	</alias>
</fontconfig>

```