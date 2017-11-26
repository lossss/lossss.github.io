---
title: python-notes
date: 2017-09-29 23:48:34
categories: python
tags: python
---
记录pyhon学习中的一些问题及解决方式 因为环境切换到了ubuntu中所以会有些ubuntu的命令
<!--more-->
## install & update
[参考](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-ubuntu-16-04)
### install & update python
```bash
sudo apt install python3 #更新也是这个

which python # 查看python的目录

alias python=python3 #设置使用python3而不是Python2
```
## pip
```bash
sudo apt-get install -y python3-pip 

pip3 install --upgrade pip

sudo -H pip install foo
```
> -H  Request that the security policy set the HOME environment variable to the home directory specified by the target user's password database entry.  Depending on the policy, this may be the default behavior.

## vscode 调试
安装插件python 按f5就可以调试

ctrl+m 然后按tab focus到debug console 上按回车 即可全键盘操作了
或者也可以直接按 ctrl+shift+y 直接切换到debug console