---
title: git-alias
date: 2017-08-13 23:39:12
categories: git
tags: git
---
git中修改别名
<!--more-->
## 修改方式
1. 直接在命令行中修改
``` bash
git config --global alias.st status
```
2. 或者找到文件
![](https://losssblog.oss-cn-hangzhou.aliyuncs.com/git-alias/1.png?x-oss-process=style/blogimage)
3. 修改对应的alias
![](https://losssblog.oss-cn-hangzhou.aliyuncs.com/git-alias/2.png?x-oss-process=style/blogimage)
4. 以下是我的alias名(仅作个人备忘)

| alias   | full name                                                                                                                               |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------|
| st      | git status                                                                                                                              |
| co      | git checkout                                                                                                                            |
| ci      | git commit -m                                                                                                                           |
| br      | git branch                                                                                                                              |
| last    | git log -1                                                                                                                              |
| lg      | git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit |
| unstage | git reset HEAD                                                                                                                          |
| me      | git merge --no-ff                                                                                                                       |
## git in zsh
| shortcuts | operation                         |
|-----------|-----------------------------------|
| gaa       | git add -all                      |
| gst       | git status                        |
| gb        | git branch                        |
| gcmsg     | git commit -m                     |
| gd        | git diff                          |
| gcb       | git checkout -b                   |
| gco       | git checkout                      |
| grhh      | git reset HEAD --hard             |
| ggp       | git push origin $(current_branch) |
| ggl       | git pull $(current_branch)        |
| gco       | git checkout                      |
| gm        | git merge                         |
## 参考文档
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375234012342f90be1fc4d81446c967bbdc19e7c03d3000
