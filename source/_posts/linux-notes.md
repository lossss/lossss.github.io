---
title: linux-notes
date: 2017-11-05 16:45:49
categories: linux
tags: linux
---
linux 备忘
<!--more-->
## 常用命令
| 命令                           | 功能                  |
| ------------------------------ | --------------------- |
| ctrl+shift+ +                  | 放大命令行字体        |
| ctrl+ -                        | 缩小命令行字体        |
| history (!200 执行200行的命令) | 查看历史命令          |
| ls 2*                          | 以2开头的文件         |
| ls 2?                          | 以2开头的文件(占一位) |
| ls 1[1-5]3.txt                 | 正则匹配              |
| ls > xxx.txt                   | ls结果保存到xxx.txt   |
| ls >> xxx.txt                  | ls结果追加到xxx.txt   |
| more xxx.txt                   | 滚屏查看文件          |
| ls -alh /bin \| more           | 管道                  |
| cd ../..                       | 上上层                |
| cd -                           | 回到上一次目录        |
| cd ~                           | 回到加速目录          |
| tree                           | 目录树                |
| mkdir A/B/C/D -p               |                       |
| rmdir                          | 删除文件夹            |
| rm C -r                        | 递归删除              |
| mv 111.txt A/222.txt           | 剪切粘贴              |
| mv 1.txt 2.txt                 | 重命名                |
| cp 111.txt A/222.txt           | 复制粘贴              |
| cp A B -r                      | 复制粘贴文件夹        |
| ln -s 1.txt 1-softlink.txt     | 软连接                |
| ln 1.txt 1.txt 1-hardlink.txt  | 硬链接                |
| cat 1.txt 2.txt >> xxx.txt     |                       |
| grep -n "ntfs" xxx.txt         | 显示包含ntfs的内容    |
| grep -v "ntfs" xxx.txt         | 不包含ntfs的内容      |
| grep "^ntfs" xxx.txt           | 以ntfs开头            |
| grep "ntfs$" xxx.txt           | 以ntfs结尾            |

## 命令行tips
参看这个[视频](https://www.bilibili.com/video/av4337389/)

| 按键   | 操作             |
| ------ | ---------------- |
| ctrl+b | 命令行向前       |
| ctrl+f | 向后             |
| alt+b  | 以单词为单位向前 |
| alt+f  | 以单词为单位向后 |
| ctrl+a | 行首             |
| ctrl+e | 行尾             |
| ctrl+u | 删除当前命令     |
| ctrl+h | 从后向前删除     |
| ctrl+k | 删除到行尾       |
| ctrl+p | 上一条命令       |
| ctrl+n | 下一条命令       |

## use oh my vsh on ubuntu

1.安装vsh
```bash
sudo apt-get install zsh
```
2.设置zsh为默认shell
```bash
sudo chsh -s $(which zsh)
```
3.重启

4.安装oh-my-zsh https://github.com/robbyrussell/oh-my-zsh

5.安装主题
```bash
vim ~/.zshrc
```
![主题设置](http://ou7k0sem6.bkt.clouddn.com/blog/171106/72gl35GKm9.png)
[主题样式查看](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)

如果出现中间图片的显示异常
![显示异常](http://ou7k0sem6.bkt.clouddn.com/blog/171106/FhBfGbgkAH.png)

6.安装powerline https://github.com/powerline/fonts

如果还是显示异常
`terminal>Preference>Profiles>myprofile(默认unmanned)>General>custom font`选择 ubuntu mono derivative Powerline Regular 当然你也可以在powerline的github页面上 Powerline Font Family 列下选择自己喜欢的字体
