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

## 常见技巧
### not

```css
ul li:not(li:last-child){
  color:red;
}
```

### img

```css
/* 将一个方形图片 显示成圆形 */
border-radius:50%
```

```html
<!-- 如果圆形图片显示有偏移则需要将图片放入div中给div加overflow -->
<div class="circular--landscape">
  <img src="xxx.jpg"/>
</div>
```

```css
.circular--landscape{
    display:inline-block;
    position:relative;
    width:200px;
    height:200px;
    overflow:hidden;
    border-radius:50%;
}

.circular--landscape img{
    width:auto;
    height:100%;
    margin-left:-50px;
}
```