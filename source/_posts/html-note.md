---
title: html-note
date: 2017-10-15T16:21:48.000Z
categories: web
tags: html
---

html 笔记

<!-- more -->

 ## 问题搜索

前端有问题 搜索时前面加MDN

## 常用标签

### table

```html
    <table width="500" height="300" align="center" cellspacing="5" cellpadding="10" border="1px">
    <caption>人员表</caption>
    <thead>
      <tr>
        <th>姓名</th>
        <th>性别</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>小明</td>
        <td>男</td>
      </tr>
      <tr>
        <td>小王</td>
        <td>女</td>
      </tr>
    </tbody>
  </table>
```
行合并: rowspan

列合并: colspan

### html5新加

datalist

```html
  <input type="text" list="star">
  <datalist id="star" class="">
    <option>jay</option>
    <option>liu</option>
    <option>xiaoming</option>
    <option>xiaoqiang</option>
  </datalist>
```

fieldset

```html
  <fieldset>
    <legend>登陆</legend>
    用户名 <input type="text"><br> 密码 <input type="password">
  </fieldset>
```



## emmet

### 文档

官方文档 <https://docs.emmet.io/>

写法对照表 <https://docs.emmet.io/cheat-sheet/>

### Emmet 语法

#### 标签

```html
div ⟹ <div></div>

foo ⟹ <foo></foo>
```

同时Emmet 还采用了css 的元素选择器

#### 后代： >

div>ul>li ⟹

```html
<div>
    <ul>
        <li></li>
    </ul>
</div>
```

#### 兄弟：+

div+p+bq ⟹

```html
<div></div>
<p></p>
<blockquote></blockquote>
```

#### 上级：^

div+div>p>span+em^bq ⟹

```html
<div></div>
<div>
    <p><span></span><em></em></p>
    <blockquote></blockquote>
</div>
```

#### 乘法：*

ul>li*5 ⟹

```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

#### 分组：()

```
div>(header>ul>li*2>a)+footer>p ⟹
```

```html
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

#### ID 和 CLASS

```
div#header+div.page+div#footer.class1.class2.class3 ⟹
```

```html
<div id="header"></div>
<div class="page"></div>
<div id="footer" class="class1 class2 class3"></div>
```

#### 自定义属性

```
td[title="Hello world!" colspan=3] ⟹
```

```html
<td title="Hello world!" colspan="3"></td>
```

#### 自增符号：$

```
ul>li.item$*5 ⟹
```

```html
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
</ul>
```

#### 改变自增基数和方向：@

```
ul>li.item$@-*5 ⟹
```

```html
<ul>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
    <li class="item2"></li>
    <li class="item1"></li>
</ul>
```

```
 ul>li.item$@3*5 ⟹
```

```html
 <ul>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
    <li class="item6"></li>
    <li class="item7"></li>
</ul>
```

#### 文本：{}

```
a[#]{Click me} ⟹
```

```html
<a href="#">Click me</a>
```

#### Lorem Ipsum(乱数假文)：lorem

```
lorem ⟹ Lorem ipsum dolor sit amet, consectetur adipisicing elit. Similique impedit quaeiure quos itaque, deserunt dolore in consequatur veniam cumque, est voluptatibus minima, velit culpa, reprehenderit aspernatur iste facilis. Rerum!
```

### Emmet的css支持

#### css属性

```
m ⟹ margin:
```

```
fz ⟹ font-size: ......
```

其实这些属性简写都不需要特意去记，你只组要按着你的思路来猜这个属性的简写就好了。

#### 属性值

```
m10 ⟹ margin: 10px; mt10 ⟹ margin-top: 10px; ......
```

多个属性值：对于有多个属性值的CSS属性，在编写时只需在属性值之间添加-：

```
m4-6 ⟹ margin: 4px 6px;
```

Emmet默认单位为px，如果你想使用其他单位就继续看下面吧

#### 单位

在Emmet中每一个单位都有其缩写形式(当然了你记不住也没关系，直接按全就好)

- p → %
- e → em
- r→ rem
- x → ex

```
 w100p ⟹ width: 100% m10p30e5x ⟹ margin: 10% 30em 5ex
```

引用于 <https://juejin.im/post/592bdebfac502e006c831d32>

## h5

