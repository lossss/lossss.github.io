---
title: vscode-setting
date: 2017-09-28 15:07:58
categories: tools
tags: vscode
---
vscode 设置
<!--more-->
## 我的设置
我的vscode 设置已经上传到[Github Gist](https://gist.github.com/lossss/a1c4db18a2482d9bfb10c43e3a6831b7)

windows下配置 Gist ID : a1c4db18a2482d9bfb10c43e3a6831b7

插件是 ~~setting sync~~ 改用 Syncing

## 常用设置

1. 隐藏菜单栏

ctrl+shift+p

view：toggle menu bar

想使用的时候按alt

2. 修改字体

在文件 首选项 设置 用户设置中加入`"editor.fontSize":17`即可

## 常用快捷键
| 快捷键(mac)                                                                                                                                                                                                               | 快捷键(win)             | 功能                                                   |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------|:-------------------------------------------------------|
|                                                                                                                                                                                                                           | ctrl+shift+p            |                                                        |
|                                                                                                                                                                                                                           | ctrl+shift+n            | 因为不能同时打开多个项目所以只能新建窗口来打开新的项目 |
|                                                                                                                                                                                                                           | shift+alt+f             | 格式化文件                                             |
|                                                                                                                                                                                                                           | ctrl+1 ctrl+2 ctrl+3    | 左中右3个编辑器的快捷键                                |
|                                                                                                                                                                                                                           | ctrl+tab                | 历史打开文件之间切换                                   |
|                                                                                                                                                                                                                           | ctrl+k然后按left或right | 编辑器换位置                                           |
|                                                                                                                                                                                                                           | alt+上/下               | 上移或下移代码                                         |
|                                                                                                                                                                                                                           | ctrl+0 或者ctrl+shift+e | focus on sidebar                                       |
|                                                                                                                                                                                                                           | ctrl+\                  | 复制分屏                                               |
| shift+cmd+m                                                                                                                                                                                                               |                         | problems                                               |
| shift+cmd+u                                                                                                                                                                                                               |                         | output                                                 |
| shift+cmd+y                                                                                                                                                                                                               |                         | debug console                                          |
| ctrl+`       |                         | terminal |                         | |                         | |                         | |                         | |                         | |                         | |                         |                                                        |
| ctrl+123                                                                                                                                                                                                                  |                         | 在已经打开的tab里面切换                                |
| ctrl+shift+i                                                                                                                                                                                                              |                         | reveal active file in side bar                         |
|                                                                                                                                                                                                                           | alt+b                   | navigateBack                                           |
|                                                                                                                                                                                                                           | alt+f                   | navigateforward                                        |
### 小tips
1.如果在编辑markdown时需要格式化表格当使用vim时可以如下操作
  * ctrl+[ 切换到normal mode
  * shift-v
  * 5k //k就是移动的下 反之向上选择就是j
  * =

## 修改的快捷键
对应修改keybindings.json 因为修改频繁 最新的修改可以参考本文置顶的github gist 在文中搜索 keybindings 就可以看到了
```json
// 将键绑定放入此文件中以覆盖默认值
[{
        "key": "ctrl+c",
        "command": "editor.action.clipboardCopyAction"
    }, {
        "key": "ctrl+x",
        "command": "editor.action.clipboardCutAction"
    }, {
        "key": "ctrl+v",
        "command": "editor.action.clipboardPasteAction"
    }, {
        "key": "ctrl+f",
        "command": "-workbench.action.terminal.focusFindWidget",
        "when": "terminalFocus"
    }, {
        "key": "ctrl+n",
        "command": "workbench.action.files.newFile",
        "when": "sidebarFocus"
    },
    {
        "key": "ctrl+b",
        "command": "workbench.action.toggleSidebarVisibility"
    },
    {
        "key": "ctrl+b",
        "command": "-workbench.action.toggleSidebarVisibility"
    },
    {
        "key": "ctrl+shift+enter",
        "command": "editor.action.triggerSuggest",
        "when": "editorHasCompletionItemProvider && editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+space",
        "command": "-editor.action.triggerSuggest",
        "when": "editorHasCompletionItemProvider && editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+shift+enter",
        "command": "toggleSuggestionDetails",
        "when": "editorTextFocus && suggestWidgetVisible"
    },
    {
        "key": "ctrl+space",
        "command": "-toggleSuggestionDetails",
        "when": "editorTextFocus && suggestWidgetVisible"
    }
]
```

## 常用插件

> 按下ctrl+shift+p 后输入 ext回车 或者点击左侧第五个图标 就可以搜索自己需要的插件了

### 通用

1. vscode-icons
> 给sidebar换上一套图标 ctrl+shift+p ->icon theme

2. output colorizer

3. guides
> 代码对齐辅助线

4. ~~没有找到 文件显示git status状态的插件(类似atom的tree-view-git-status)~~ 最新版本已经自带此功能

5.~~Settings Sync~~(这个有点问题已经换用Syncing)
> 同步设置
这个插件如果同步报错的话
```
ctrl+shift+p
sync:reset extension settings
在user settings 里面修改下gistid
```
6. Search Docsets
> 查看文档  需要提前安装 velocity 或者 zeal 快捷键 shift+F1 mac中对应的插件为dash

7. text table
方便生成 markdown table 默认快捷键ctrl+q
### vim

1. vim
这个插件可以实现vim中的大多数操作介绍几个比较有用的(安装vim插件后自带的,无需其他插件)

    1. [multi-cursor-mode](https://github.com/VSCodeVim/Vim#%EF%B8%8F-multi-cursor-mode)
        先用v选择需要修改的单词在用 cmd+d 向下选中同样单词 然后修改
    1. [vim-surround](https://github.com/VSCodeVim/Vim#vim-surround)
| Surround Command                       | Description                                                           |
|:---------------------------------------|:----------------------------------------------------------------------|
| d s \<existing char\>                  | Delete existing surround                                              |
| c s \<existing char\> \<desired char\> | Change surround|existing to desired                                   |
| y s \<motion\> \<desired char\>        | Surround something with|something using motion (as in "you surround") |
| S \<desired char\>                     | Surround when in visual modes|(surrounds full selection)              |

        hint: ysaw)
    1.[vim-easymotion](https://github.com/VSCodeVim/Vim#vim-easymotion)
        这是一个快速移动插件,默认的\<leader>是 \\

| command               | description             |
|:----------------------|:------------------------|
| \<leader>\<leader> s  | Search character        |
| \<leader>\<leader> 2s | Search 2 characters     |
| \<leader>\<leader> w  | Start of word forwards  |
| \<leader>\<leader> b  | Start of word backwards |
| \<leader>\<leader> j  | Start of line forwards  |
| \<leader>\<leader> k  | Start of line backwards |

2. relative-line-numbers

#### tips
zc 折叠代码后jk移动时会自动打开 要避免的话 setting 里面加`"vim.foldfix": true`

### python

1. python
如果需要提示时输出括号 在setting中加上`"python.autoComplete.addBrackets": true`
2. magicpython
> python文件着色器

### markdown

1.  vscode markdown preview enhanced
安装好后 ctrl+shift+m 预览 或者也可以用vs自带的ctrl+k v 打开预览

2. table formatter
格式化table 其实我更喜欢 atom里面的 markdown table formatter

安装后 ctrl+shift+p -> table:format all

3. snippet for json

| Snippets | Content                                                                                                    |
|:---------|:-----------------------------------------------------------------------------------------------------------|
| obj      | Create a JSON object                                                                                       |
| objc     | Create a JSON object ending with comma                                                                     |
| arr      | Create a JSON array                                                                                        |
| arrc     | Create a JSON array ending with comma                                                                      |
| pair     | Create JSON key/value pair                                                                                 |
| pairc    | Create JSON key/value pair ending with comma                                                               |
| paircln  | Create JSON key/value pair ending with comma and jumping to next line. Not recommended for complex "value" |

## debug

### python

安装python插件之后 按f5 就可以进行调试
当需要使用input 或者需要输出图片的时候 在左上选择integrated terminal/console 在运行即可

## ubuntu 下更新vscode
1. 到下载页面下载最新版本.deb
2. 执行以下命令 
```bash
sudo dpkg -r code
sudo dpkg -i code_downloaded_package.deb #用下载的最新的deb的名字
```
## tips

### [Launching from the Command Line](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)
