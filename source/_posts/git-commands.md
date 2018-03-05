---
title: git-commands
date: 2017-09-08 19:16:26
categories: git
tags: git
---
常用的git 命令备忘
<!--more-->
![](http://ou7k0sem6.bkt.clouddn.com/gitcheatsheet.png)

## 终极杀招
任何命令有问题就直接在后面 --help 直接到官方文档那里不会点哪里
比如
```
git commit --help
git help commit
```
## 第一次装git连接github时需要的命令
```bash
git config --global user.name "losss"

git config --global user.email "stdiolosss@gmail.com"  

# /home/losss/.ssh/id_rsa.pub
ssh-keygen -t rsa -C "stdiolosss@gmail.com"
# 测试连接
ssh -T git@github.com

如果提示
```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0670 for '/home/losss/.ssh/id_rsa' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "/home/losss/.ssh/id_rsa": bad permissions
Permission denied (publickey).
```
运行如下命令
```bash
 chmod 600 /home/losss/.ssh/id_rsa
```

git clone ...
```

commit 信息写错了 需要修改
```
git commit --amend
```
## 常用命令
```
git status # 查看工作区和缓冲区状态
git add --all # 将工作区修改暂存到缓冲区
git commit -m"<comment>" # 提交到仓库
git push origin master # 推送到远程分支
```

git ignore(并不常用 但是我不知道怎么分类了)

检查.gitignore 文件规则
```
git check-ignore -v App.class
```
## 版本的回退与前进
回退到上一个版本 如果是上上个版本就是HEAD^^
```
git reset --hard HEAD^
```

回到固定的版本
> 6位 hash 就可以
```
git reset --hard <commit-hash>
```

what is --hard
> Resets the index and working tree. Any changes to tracked files in the working tree since <commit> are discarded.

查看命令历史
```
git reflog
```

## 分支的操作
创建并切换到新分支
```
git checkout -b <branch-name>
```
创建但是不切换分支
```
git branch new <branch-name>
```

删除分支
```
git branch -d test
```

--no-ff 这样删除分支之后再git log 里面仍然可以显示出分支信息
```
git merge --no-ff -m "merge with no-ff" dev
```

## 撤销操作
撤销在add之前的修改 当然也可以用来回复被rm掉的文件
```
git checkout --readme.txt
```

恢复暂存区的所有文件到工作区
```
git checkout .
```

撤销add
```
git reset HEAD <file>
```

去掉某个commit
```
git revert <commit-bash>
```

git stash
这个命令是暂时封存工作空间的状态 [详细查看](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000)
如果有多个stash的时候要小心 如果不加参数默认就会对最近的一次操作
```
git stash
```

还原最近一次操作 并且不删除标记
```
git stash apply
```

如果需要还原对应序号的话
```
git stash apply --index 4
```

会还原最近一次的保存 会删除标记
```
git stash pop
```

删除最近的一次的保存
```
git stash drop
```

显示list
```
git stash list
```

显示对应保存中的内容 可以对应list中的序号
```
git stash show 4
```
git stash 使用例子
1. 本地有修改，能不能先git pull
```
git stash # 工作区修改暂存
git pull  # 更新分支
git stash pop # 暂存修改恢复到工作区
```
2. 有bug需要修改可以先使用git stash 把现有的工作保存起来然后切换到别的分支修改之后再切回来使用git stash pop 还原之前的工作 在多人协作的情况下有用

## 关联远程仓库
关联远程仓库
```
git remote add <name> <git-repo-url>
```
查看远端关联的仓库
```
git remote -v
```

强制推送本地版本到远端
```
git push origin master -f
```

远程分支被别人更新了，你需要更新代码
```
git pull origin <branch-name>
```
重新设置远端地址
```
git remote set-url origin <your-git-url>
```
