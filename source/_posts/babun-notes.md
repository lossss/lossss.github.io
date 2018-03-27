---
title: babun-notes
date: 2017-11-06 18:43:18
categories: tools
tags: babun
---
babun on windows10
<!--more-->
## download
http://babun.github.io
## set oh my dash theme

1. download [DejaVu Sans Mono](https://github.com/powerline/fonts/blob/master/DejaVuSansMono/DejaVu%20Sans%20Mono%20for%20Powerline.ttf)

2. `vim ~/.minttyrc`  copy/paste the below into the file
```
BoldAsFont=no
Columns=150
Rows=55
Font=DejaVu Sans Mono for Powerline
FontHeight=10
Transparency=low

ForegroundColour=#A0A0A0
BackgroundColour=#1B1D1E
CursorColour=#A0A0A0
Black=#1B1D1E
Red=#F92672
Green=#82B414
Yellow=#FD971F
Blue=#268BD2
Magenta=#8C54FE
Cyan=#56C2D6
White=#CCCCC6
BoldRed=#FF5995
BoldBlack=#505354
BoldGreen=#B7EB46
BoldYellow=#FEED6C
BoldBlue=#62ADE3
BoldMagenta=#BFA0FE
BoldCyan=#94D8E5
BoldWhite=#F8F8F2
```

3. `vim ~/.zshrc`
```
 ZSH_THEME="agnoster"
```
4. settings about mouse

![mouse settings](http://ou7k0sem6.bkt.clouddn.com/babun-notes/1.png)

use shift and left mouse to choose

use right mouse to open menu

4. reload the babun

![cool](http://ou7k0sem6.bkt.clouddn.com/babun-notes/2.png)

https://www.sorendam.com/take-control-of-your-console-in-windows-with-babun-oh-my-zsh-and-powerline-fonts/

## configure Babun/ZSH for the integrated terminal in vscode
please use ZSH_THEME="babun" or other themes because the theme "agnoster" has some problems
1.
```
"terminal.integrated.shell.windows": "C:\\Users\\losss\\.babun\\cygwin\\bin\\zsh.exe"
```
2. Add on command in ~/.babunrc :
```
cd $OLDPWD
```
![end](http://ou7k0sem6.bkt.clouddn.com/babun-notes/3.png)

use left mouse button to choose and copy then click the right mouse button to paste

## Package manager
Babun provides a package manager called `pact`. It is similar to 'apt-get' or 'yum'. Pact enables installing/searching/upgrading and deinstalling cygwin packages with no hassle at all. Just invoke pact --help to check how to use it.

## tips
### alias
```bash
vim ~/.zshrc
alias gm="git merge --no-ff "
```
### 中文乱码 
使用git add添加要提交的文件的时候，如果文件名是中文，会显示形如 274\232\350\256\256\346\200\273\347\273\223.png 的乱码。 

解决方案：在bash提示符下输入： 
```
  git config --global core.quotepath false
```
core.quotepath设为false的话，就不会对0x80以上的字符进行quote。中文显示正常。 