---
title: vim-notes
date: 2017-08-13 23:38:03
categories: vim
tags: vim
---
# vim安装及配置
## 安装
这里使用[neovim](https://github.com/neovim/neovim)
1. install
  ```bash
  brew install neovim
  ```

2. upgrade
```bash
brew update
brew upgrade neovim
```

3. use
  ```bash
  nvim
  ```

## 配置
1. neovim 配置文件路径是 `~/.config/nvim/init.vim`(没有的话自己新建)这个的内容和vim的.vimrc内容是一样的
1. 换个主题 这里我用的是[Dracula](https://draculatheme.com/)这种主题很多自己找喜欢的就行
    1. 先把对应的主题下载下来然后把主题的.vim文件放在`~/.config/nvim/colors`下(或者`~/.vim/colors`下)
    1. 在init.vim 里面加入
      ```vim
      syntax on
      color dracula
      ```
     如果用zsh的同学需要注意你的zsh主题最好要和neovim主题一样不然显示可能会有点问题
1. 可以在github上看一些高手的init.vim设置

https://github.com/TimothyYe/mydotfiles/blob/master/neovim/.config/nvim/init.vim


## 插件
先装 [vim-plug](https://github.com/junegunn/vim-plug)
装好后在`~/.config/nvim/init.vim` 里面写需要的插件下面是neovim的demo具体的查看官方文档 这里如果begin里面不写地址的话默认的是`~/.config/nvim/`这个路径

```vim
call plug#begin('~/.local/share/nvim/plugged')
" My Bundles:
Plug 'kien/ctrlp.vim'
call plug#end()
```

### 推荐的插件
1. [vim-plug](https://github.com/junegunn/vim-plug) Vim的插件管理器，支持并发安装和更新
1. [CtrlP](https://github.com/kien/ctrlp.vim) 不可缺少的快速跳转插件，它可以快速的帮助我们找到项目中的文件。在vim normal模式下，按下ctrl+p，然后输入你要寻找的文件就行了。
1. Ack 全文搜索插件，可以在当前打开的项目中进行源码的全文搜索，并可以在搜索结果中方便的切换和打开源码文件，十分方便。
1. NERDTree Vim中的文件管理器，方便编辑文件，创建目录，删除和修改文件等等……
1. NERDTreeCommenter 方便的用来注释代码的插件
1. TagBar 查看当前代码文件中的变量和函数列表的插件，可以切换和跳转到代码中对应的变量和函数的位置
1. AutoPairs 自动补全括号的插件，包括小括号，中括号，以及花括号，可以提升编码效率
1. Surround 快速给词加环绕符号,例如单引号/双引号/括号/成对标签等的插件
1. Vim-Airline Vim状态栏插件，包括显示行号，列号，文件类型，文件名，以及Git状态
1. EasyMotion 在当前文件中快速移动光标到指定查找位置的插件，十分方便和高效
1. deoplete 自动补全插件，写代码必备，有了这个插件，就有了IDE的感觉
1. Vim-Startify Vim启动首屏自定义插件，让你的Vim启动后显示别具一格的首屏样式
1. Vim-Indent-Guides 显示代码对齐的引导条
1. Accelerated-Smooth-Scroll 顾名思义，让Ctrl+F,Ctrl+B的滚屏来得更顺滑一些……
1. YouDao-Translater Vim中的有道翻译插件
1. Matrix-ScreenSaver Vim中的黑客帝国屏幕保护插件，很酷很炫


### 管理dotfiles
使用[homeshick](https://github.com/andsens/homeshick)
常用命令
```bash
homeshick generate dotfiles #创建
homeshick track dotfiles .bashrc #添加
homeshick clone git@github.com:lossss/dotfiles.git #新机拷贝
```
# vim 中常用的快捷键

<!--more-->

## 移动

超常用的hjkl就不必多说了
| 快捷键    | 功能                                            |
|:----------|:------------------------------------------------|
| 0         | （数字 0）移动光标至本行开头                    |
| ^         | 移动光标至本行第一个非空字符处                  |
| $         | 移动到行尾                                      |
| gg        | 最上面一行                                      |
| G         | 最下面一行                                      |
| NG        | 跳到第N行(绝对行数)                             |
| :15       | 跳转到15行                                      |
| w         | 向前移动一个词 （上一个字母和数字组成的词之后） |
| e         | 跳到这个单词的末尾                              |
| b         | 向后移动一个词 （下一个字母和数字组成的词之前） |
| f         | 搜索例如fw就会移动到这一行中出现的第一个w       |
| %         | 跳到对应的(, (, [ 处                            |
| *         | 跳到当前光标的下一个(上一个) 相同单词的地方     |
| ctrl+f    | full page forward                               |
| ctrl+b    | full page back                                  |
| ctrl+u    | half page forward                               |
| ctrl+d    | half page back                                  |
| ctrl+v    | visual block mode                               |
| shift + ] | 移动到下一个空行                                |
| shift + [ | 移动到上一个空行                                |
| vii       | 全选                                            |

w w e e 的区别
![](http://ou7k0sem6.bkt.clouddn.com/vim-notes/1.jpg)

## 常用补充
| 快捷键                  | 功能                                                         |
|:------------------------|:-------------------------------------------------------------|
| i                       | 词前插入                                                     |
| shift+i                 | 行首插入                                                     |
| a                       | 词后插入                                                     |
| shift+a                 | 行尾插入                                                     |
| .                       | .可以重复执行上个指令 比如fw之后.就会继续移动到下一个w的位置 |
| d                       | 删除至行尾 d$的缩写                                          |
| x                       | 删除当前的字符                                               |
| x                       | 向前删除                                                     |
| s                       | 替换 按下之后会删除当前的字符并进入insert模式                |
| 3dd                     | 剪切3行                                                      |
| p                       | 黏贴                                                         |
| ctrl+shift+v / 鼠标中键 | 从clipboard粘贴                                              |
| u                       | 撤销相当于ctrl+z                                             |
| ctrl+r                  | 相当于ctrl+y                                                 |
| ZZ                      | 保存并退出                                                   |
| dt"                     | 删除直到"                                                    |
| J                       | 删除换行符，合并两行                                         |
| \< \>                   | 调整代码缩进                                                 |
| =                       | 自动格式化代码缩进                                           |
| zc                      | 折叠代码                                                     |
| zo                      | 展开带代码                                                   |
| shift+v                 | 选择当前行                                                   |
| shift+d                 | 删除至行尾                                                   |

## text-object

### a和i的区别：

an object：包含尾部间隔空格
inner object：只是内容本身，不包含尾部单词间隔空格

### word / sentence / paragraph 
| textobject | 说明      |
|:-----------|:----------|
| w          | word      |
| s          | sentence  |
| p          | paragraph |

### block / Block
| textobject | 说明              |
|:-----------|:------------------|
| ]/[        | [] block          |
| )/(、b     | block             |
| >/<、>/<   | <> block          |
| }/{、B     | Block             |
| t          | tag block：<> </> |

### visual mode
在可视选择模式下，可以以 v 做前缀，a 或 i 限定边界，后续指定操作对象，来实现针对文本对象的选择：

| 指令 | 说明                                                |
|:-----|:----------------------------------------------------|
| viw  | 选中单词                                            |
| vis  | 选中句子                                            |
| vit  | 选中html标签内的内容                                |
| vip  | 选中段落                                            |
| vi(  | 选中圆括号中的内容                                  |
| vi[  | 选中中括号之间的内容                                |
| v2i{ | 选中两层大括号之间的所有内容 数字限定选择的嵌套层数 |
| v3aw | 选择三个单词（包含中间的2个间隔空格）               |
| v3iw | 选择三个单词（2个单词+间隔空格）                    |
另外，可将 v 选择操作指令替换为 c、x、d、y 等操作符(operator)，来针对文本对象操作

## 小tips
1. 多行同时编辑:

按 ctrl+v ，进入 Visual Block mode

然后按hjkl 选择对应的行 当然你也可以用 5k等等选择 

然后 shift+i(单词之前) 或者 shift+a(单词之后) 

如果要在多行行首插入的话要先shift+v 然后 选择多行 再按shift+i 行尾就是shift+a

2. 全选复制
esc后 ggyG

3. 全选删除
esc后 dG

4. 选中当前的单词
 viw    //inner word
 diw //删除当前单词

5. 在vim中
 esc = ctrl+[ 当然 ctrl+v 也可以用来切换模式

6. shift+/ 搜索
 *向前搜索 #向后搜索

7. 修改 gem 'hello' ''中的内容
ci'
关于这个可以参考 [一起来说vim语](http://www.jianshu.com/p/a361ce8c97bc)

8. 注释代码 行注释gc2j 块注释gC2j

9. 清空一行 而不删除这行
normal mode 0D // 0 至行首 shift+d 清空
10. 插入新的一行而不进入insert mode
yy一个空行再p

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

## [vscode vim plugin](https://github.com/VSCodeVim/Vim)
### [vim-surround](https://github.com/VSCodeVim/Vim#vim-surround)
| Surround Command                       | Description                                                            |
|:---------------------------------------|:-----------------------------------------------------------------------|
| d s \<existing char\>                  | Delete existing surround                                               |
| c s \<existing char\> \<desired char\> | Change surround |existing to desired                                   |
| y s \<motion\> \<desired char\>        | Surround something with |something using motion (as in "you surround") |
| S \<desired char\>                     | Surround when in visual modes |(surrounds full selection)              |

hint: ysaw)

## 参考
https://linux.cn/article-8144-1.html

http://www.oschina.net/translate/learn-vim-progressively

https://computers.tutsplus.com/tutorials/vim-for-beginners--cms-21118

http://col.dog/2015/12/13/vim-tutorials-006-text_objects/

https://xiaozhou.net/learn-the-command-line-vim-2018-08-08.html