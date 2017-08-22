---
title: Atom-setting
date: 2017-08-17 16:00:20
categories: atom
tags: atom
---
Atom 的基础设置
<!--more-->
我们从下载完成后开始设置的配置
以下有很多是个人设置 选择自己喜欢的设置就好
## Atom自身设置
### 在编辑中像sublime一样会用点显示空格
<font color= "red">`File->Settings`</font>

![](http://ou7k0sem6.bkt.clouddn.com/showinvisible.png)

勾选show Invisible 即可

### 修改tab为4个空格
`File->Settings`
![](http://ou7k0sem6.bkt.clouddn.com/tab.png)

修改tab length 为4

### 删除中间的竖线
竖线是提示超过改线可能会导致自动换行 如果想要隐藏
`File->Stylesheet`增加以下代码
``` css
atom-text-editor::shadow .wrap-guide {
  //隐藏右边的白线
  visibility: hidden;
}
```
## 常用插件
请看我的另外一篇博客  {% post_link atom-plugins %}
## 关于主题
theme里面是有很多主题 但是我用了之后发现默认的markdown语法不高亮了 现在用的配置是 UI theme:One synatx Theme: Dark base16-tomorrow-dark-theme
