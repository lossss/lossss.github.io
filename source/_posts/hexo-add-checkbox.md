---
title: hexo-add-checkbox
date: 2017-08-09 18:31:38
categories: hexo
tags: hexo
---
在hexo中添加复选框
<!--more-->
## 配置

1. 修改 hexo 的 markdown 渲染引擎：

``` bash
cd hexo-blog.github.io/ # 首先进入你的 hexo 的根目录
npm un hexo-renderer-marked --save # 卸载 hexo 默认的 markdown 渲染引擎
npm i hexo-renderer-markdown-it --save # 安装 markdown-it
```
2. 下载 markdown-it 的 markdown-it-checkbox 插件：
``` bash
cd node_modules/hexo-renderer-markdown-it/
npm install markdown-it-checkbox --save
```
3. 在 hexo 的全局配置文件 _config.yml 添加以下：
``` yml
# Markdown-it config
## Docs: https://github.com/celsomiranda/hexo-renderer-markdown-it/wiki
markdown:
  render:
    html: true # Doesn't escape HTML content so the tags will appear as html.
    xhtmlOut: false # Parser will not produce XHTML compliant code.
    breaks: true # Parser produces `<br>` tags every time there is a line break in the source document.
    linkify: false # Returns text links as text.
    typographer: true # Substitution of common typographical elements will take place.
    quotes: '“”‘’' # "double" will be turned into “single”
                   # 'single' will be turned into ‘single’
  plugins:
    - markdown-it-abbr
    - markdown-it-checkbox # 本行启用了 checkbox 插件
    - markdown-it-emoji # 如果你想在 md 中使用 emoji 表情的话，需要另外下载相关插件
    - markdown-it-footnote
    - markdown-it-ins
    - markdown-it-sub
    - markdown-it-sup
  anchors:
    level: 2 # Minimum level for ID creation. (Ex. h2 to h6)
    collisionSuffix: 'v' # A suffix that is prepended to the number given if the ID is repeated.
    permalink: true # If true, creates an anchor tag with a permalink besides the heading.
    permalinkClass: header-anchor # Class used for the permalink anchor tag.
    permalinkSymbol: ¶ # The symbol used to make the permalink.
```
## 显示效果
- [x] 测试
- [ ] 测试
## 修改复选框的样式
1. 找到自定义样式的文件：themes/next/source/css/_custom/ 路径下的 custom.styl 。
2. 添加以下样式：
``` code
input[type="checkbox"] {
  display: none !important; // by imo: to overwrite styles in DuoShuo-Comments-Plugin
}
input[type="checkbox"] + label::before {
  content: '\a0';
  display: inline-block;
  margin-right: .2em;
  border: 1px solid;
  border-radius: .2em;
  width: .8em;
  height: .8em;
  vertical-align: .1em;
  text-indent: .1em;
  line-height: .7;
}
input[type="checkbox"]:checked + label::before {
  content: '\2713';
}
```
## 使用 markdown-it 的 anchors 功能带来的副作用
使用 markdown-it 的 anchors 功能后，文章目录（Table of Content, TOC）中每个章节标题前均出现永久链接符号（默认为 ¶ ）。

1. 找到 hexo 定义 toc 函数的文件：/node_modules/hexo/lib/plugins/helper 目录下的 toc.js 。
2. 修改生成标题文本的代码行 var text = $(this).text(); 为如下即可：
``` javascript
var text = $(this).text().slice(1);// by imo: remove markdown-it's anchor character in TOC
```
## 参考文档
Hexo 的 markdown-it 渲染引擎和其相关插件 http://baishusama.github.io/2016/12/24/hexo-render-markdown-it-and-its-plugins/
