---
title: emoji
date: 2017-08-07 18:55:18
categories: hexo
tags: [hexo,emoji]
---
在 hexo中使用emoji
<!--more-->
1. 安装 markdown-it
```bash
npm un hexo-renderer-marked --save
npm i hexo-renderer-markdown-it --save
```
2. 没有emoji的表情插件，因此要安装 markdown-it-emoji
``` bash
npm install markdown-it-emoji --save
```
3. 配置config.yml
```
markdown:
  render:
    html: true
    xhtmlOut: false
    breaks: true
    linkify: true
    typographer: true
    quotes: '“”‘’'
  plugins:
    - markdown-it-abbr
    - markdown-it-footnote
    - markdown-it-ins
    - markdown-it-sub
    - markdown-it-sup
    - markdown-it-emoji
  anchors:
    level: 2
    collisionSuffix: 'v'
    permalink: true
    permalinkClass: header-anchor
    permalinkSymbol: ¶
```

:blush: :laughing:

[更多emoji参考](https://github.com/guodongxiaren/README/blob/master/emoji.md)
