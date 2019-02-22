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
if you want to use other themes please let the theme file into `~/.oh-my-zsh/themes/`
```
 ZSH_THEME="agnoster"
```
4. settings about mouse

![mouse settings](https://losssblog.oss-cn-hangzhou.aliyuncs.com/babun-notes/1.png?x-oss-process=style/blogimage)

use shift and left mouse to choose

use right mouse to open menu

4. reload the babun

![cool](https://losssblog.oss-cn-hangzhou.aliyuncs.com/babun-notes/2.png?x-oss-process=style/blogimage)

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
![end](https://losssblog.oss-cn-hangzhou.aliyuncs.com/babun-notes/3.png?x-oss-process=style/blogimage)

use left mouse button to choose and copy then click the right mouse button to paste

## Package manager
Babun provides a package manager called `pact`. It is similar to 'apt-get' or 'yum'. Pact enables installing/searching/upgrading and deinstalling cygwin packages with no hassle at all. Just invoke pact --help to check how to use it.
