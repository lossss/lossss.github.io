---
title: git-commands
date: 2017-09-08 19:16:26
categories: git
tags: git
---
常用的git 命令备忘
<!--more-->
![](http://ou7k0sem6.bkt.clouddn.com/gitcheatsheet.png)

终极杀招
任何命令有问题就直接在后面 --help 直接到官方文档那里不会点哪里

回退到上一个版本 如果是上上个版本就是HEAD^^
> git reset --hard HEAD^

回到固定的版本
> git reset --hard 3628164

what is --hard
> Resets the index and working tree. Any changes to tracked files in the working tree since <commit> are discarded.

查看命令历史
> git reflog

撤销在add之前的修改 当然也可以用来回复被rm掉的文件
> git checkout --readme.txt

撤销add
> git reset HEAD <file>

创建并切换到新分支
> git checkout -b dev

删除分支
> git branch -d test

--no-ff 这样删除分支之后再git log 里面仍然可以显示出分支信息
> git merge --no-ff -m "merge with no-ff" dev

git stash
这个命令是暂时封存工作空间的状态 [详细查看](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000)
如果有多个stash的时候要小心 如果不加参数默认就会对最近的一次操作
> git stash

还原最近一次操作 并且不删除标记
> git stash apply

如果需要还原对应序号的话
> git stash apply --index 4

会还原最近一次的保存 会删除标记
> git stash pop

删除最近的一次的保存
> git stash drop

显示list
> git stash list

显示对应保存中的内容 可以对应list中的序号
> git stash show 4

git ignore
检查.gitignore 文件规则
> git check-ignore -v App.class
