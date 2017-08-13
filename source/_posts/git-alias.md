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
![](http://ou7k0sem6.bkt.clouddn.com/git-alias.png)
3. 修改对应的alias
![](http://ou7k0sem6.bkt.clouddn.com/git-alias2.png)
4. 以下是我的alias名(仅作个人备忘)

|  alias  |                                                                full name                                                                |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| st      | git status                                                                                                                              |
| co      | git checkout                                                                                                                            |
| ci      | git commit -m                                                                                                                           |
| br      | git branch                                                                                                                              |
| last    | git log -1                                                                                                                              |
| lg      | git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit |
| unstage | git reset HEAD                                                                                                                          |
## 参考文档
git 别名配置 <https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375234012342f90be1fc4d81446c967bbdc19e7c03d3000>
