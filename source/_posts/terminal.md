---
title: terminal
date: 2018-08-11 21:03:22
categories: terminal
tags: zsh
---
主要是iterm2下的bash和zsh的一些常用技巧和插件总结
<!--more-->

## iterm2 设置
这里只列举一些重要设置其他的可以 [参考这里](https://blog.biezhi.me/2018/11/build-a-beautiful-mac-terminal-environment.html)

1. 字体安装
配合主题powerlevel9k 需要安装字体

2. 安装主题

```bash
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
```

3. 修改zsh主题

```bash
ZSH_THEME="powerlevel9k/powerlevel9k"
```

4. 安装字体

```bash
brew tap caskroom/fonts
brew cask install font-hack-nerd-font
```

5. 修改配置.zshrc 中添加

```bash
POWERLEVEL9K_MODE="nerdfont-complete"
# Customise the Powerlevel9k prompts
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(ssh dir vcs newline status)
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=()
POWERLEVEL9K_PROMPT_ADD_NEWLINE=true
```

6. 使修改生效

```bash
source ~/.zshrc
```

## 命令行tips
参看这个[视频](https://www.bilibili.com/video/av4337389/)

| 按键   | 操作             |
|:-------|:-----------------|
| ctrl+b | 命令行向前       |
| ctrl+f | 向后             |
| alt+b  | 以单词为单位向前 |
| alt+f  | 以单词为单位向后 |
| ctrl+a | 行首             |
| ctrl+e | 行尾             |
| ctrl+u | 删除当前命令     |
| ctrl+h | 从后向前删除     |
| ctrl+d | 从前向后删除     |
| alt+d  | 删除一个单词     |
| ctrl+k | 删除到行尾       |
| ctrl+p | 上一条命令       |
| ctrl+n | 下一条命令       |
| ctrl+r | 搜索历史命令     |
| ctrl+l | 清屏             |

iterm2 的常用快捷键

```bash
新建标签：command + t

关闭标签：command + w

切换标签：command + 数字 command + 左右方向键

切换全屏：command + enter

查找：command + f
```

# 常用插件

1. [autojump](https://github.com/wting/autojump)
如果你用的oh-my-zsh 只需要在`.zshrc`里面 配置plugins=(autojump) 即可
快捷键 `j foo`
注: autojump 只能jump到已经打开过一次后的目录

1. [tmux](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)
   1. 修改配置 `~/.tmux.conf` 之后 使用`tmux source-file ~/.tmux.conf`使其生效 我设置了一个快捷键  `tmrl`
   1. 值得参考的文章 http://louiszhai.github.io/2017/09/30/tmux/
   1. tmux 里使用复制粘贴 配置里面加一行`set -g mouse on` 在iterm2 `Preference->General->copy to pasteboard to selection` 然后在按住option后选择区域 最后粘贴即可
   1. sessions should be nested with care, unset $TMUX to force 输入 `unset TMUX`
   1. 以下是个人备份不是默认快捷键
1. [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
    1. 安装
    ```bash
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ```

    2. 设置

    ```bash
    plugins=( [plugins...] zsh-autosuggestions)
    ```

1. [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
    1. 安装

    ```bash
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```

    2. 设置

    ```bash
    plugins=( [plugins...] zsh-syntax-highlighting)
    ```

| 按键   | 操作         |
|:-------|:-------------|
| -      | 垂直分       |
| \      | 水平分       |
| x      | 关闭当前窗口 |
| z      | 最大化窗口   |
| ctrl+d | 关闭窗口     |

常用指令

```bash
tmux new -s demo # 新建一个名称为demo的会话
tmux a -t demo # 进入到名称为demo的会话
tmux kill-session -t demo # 关闭demo会话
tmux kill-server # 关闭服务器，所有的会话都将关闭
tmux ls # 查看所有会话，提倡使用简写形式

Sessions
:new<CR>  new session
s  list sessions
$  name session

Windows
c  create window
w  list windows
n  next window
p  previous window
f  find window
,  name window
&  kill window
```

>一般工作模式 是1个session里面开多个window 然后一个window开nvim 其他的可以跑命令 可以用 prefix+n prefx+p 切换window

Copy Mode
需要在配置文件里面加入
`setw -g mode-keys vi`和`bind-key -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "pbcopy"`
1. PREFIX [ 
2. 空格开始选择
3. y复制并退出/回车直接退出

去掉小圆点
```bash
tmux a -d #命令

`: a -d #快捷键
```
在 Preferences > Appearance 里有个「 show tab bar even when there is only one tab 」的 toggle

# 参考

1. <http://louiszhai.github.io/2017/09/30/tmux/#%E5%AF%BC%E8%AF%BB>

1. <https://gist.github.com/MohamedAlaa/2961058>
