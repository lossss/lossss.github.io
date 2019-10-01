---
title: css-notes
date: 2017-10-31 23:15:32
categories: web
tags: css
---
css 备忘
<!--more-->
## [UI设计稿全自动切图和标注的工具推荐](https://github.com/jawil/blog/issues/11)

! ps 有钱买个mac

## ps插件
[cutterman](http://www.cutterman.cn/zh/cutterman_usage)

## 常用语法

### 选择器

#### 伪类选择器

```css
a:link
a:visited
a:hover
a:active
//其他标签也可以用
p:hover
//获取焦点
input:focus
//被选择
p::selection

```

#### 伪元素

```css
p:first-letter
p:first-line

//before 结合content使用
//紧随p标签后面的位置
p:before {
  content:"出现在段落最前面"
}

p:after{
  content:"出现在段落最前面"
}

```

#### 属性选择器

```css

```