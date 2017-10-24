---
title: vim
date: 2017-08-13 23:38:03
categories: vim
tags: vim
---
# vim 中常用的快捷键

<!--more-->

## 移动

超常用的hjkl就不必多说了

| 快捷键 | 功能                                            |
| ------ | ----------------------------------------------- |
| 0      | （数字 0）移动光标至本行开头                    |
| ^      | 移动光标至本行第一个非空字符处                  |
| $      | 移动到行尾                                      |
| gg     | 最上面一行                                      |
| NG     | 跳到第N行(绝对行数)                             |
| :15    | 跳转到15行                                      |
| G      | 移动至文件末尾                                  |
| w      | 向前移动一个词 （上一个字母和数字组成的词之后） |
| W      | 向前移动一个词 （以空格分隔的词）               |
| e      | 跳到这个单词的末尾                              |
| E      | 跳到这个单词的末尾.                             |
| b      | 向后移动一个词 （下一个字母和数字组成的词之前） |
| f      | 搜索例如fw就会移动到这一行中出现的第一个w       |
| %      | 跳到对应的(, (, [ 处                            |
| *      | 跳到当前光标的下一个(上一个) 相同单词的地方     |

w W e E 的区别
![](http://ou7k0sem6.bkt.clouddn.com/vim01.jpg)

## 常用补充
| 快捷键                  | 功能                                                               |
| ----------------------- | ------------------------------------------------------------------ |
| ;                       | 分号可以重复执行上个指令 比如fw之后分号就会继续移动到下一个w的位置 |
| D                       | 删除至行尾 d$的缩写                                                |
| x                       | 删除当前的字符                                                     |
| s                       | 替换 按下之后会删除当前的字符并进入insert模式                      |
| 3dd                     | 剪切3行                                                            |
| p                       | 黏贴                                                               |
| ctrl+shift+v / 鼠标中键 | 从clipboard粘贴                                                    |
| u                       | 撤销相当于ctrl+z                                                   |
| ctrl+r                  | 相当于ctrl+y                                                       |
| ZZ                      | 保存并退出                                                         |
| dt"                     | 删除直到"                                                          |
| J                       | 删除换行符，合并两行                                               |
| \< \>                   | 调整代码缩进                                                       |
| =                       | 自动格式化代码缩进                                                 |
| zc                      | 折叠代码                                                           |
| za                      | 展开带代码                                                         |


## 小tips
1. 多行行尾同时插入:

按 \<C-v\>，进入 Visual Block mode，按 G 到末行，按 $ 到所有行的行尾，按 A 在行尾添加，输入添加的内容（只有第一行会显示），按 \<ESC\> 退出编辑。


## vim in terminal

### .vimrc
在~/.vimrc(没有可以自己新建)加入以下内容
这个就是vim的配置文件
```
set number
set relativenumber
set hlsearch
```
这样启动vim时就会加载这些设置 当然一些大佬也会共享自己的配置到github上
这里列出的几个只是冰山一角
### Search and Replace
hlsearch
> You can search by using the / command in Normal mode. By typing /This, you will see all of the This words

> By typing n, your cursor goes to the next occurrence of the search pattern. By using N, you can go back to a previous occurrence.

> The format is /\<search pattern\>/\<replace pattern\>/gi where the \<search pattern> and the \<replace pattern\> are standard regular expressions.The i after the g makes the search case insensitive. An I would make the search case sensitive. The g makes the substitution global in the line. Without the g, it performs the substitution once per line

## 参考
https://linux.cn/article-8144-1.html

http://www.oschina.net/translate/learn-vim-progressively

https://computers.tutsplus.com/tutorials/vim-for-beginners--cms-21118
