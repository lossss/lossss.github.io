---
title: intellij-idea-setting
date: 2017-10-07 23:46:21
categories: tools
tags: intellijidea
---
intellijidea 设置备忘
<!--more-->
## 一些小特性

### idea是实时保存的所以没有必要ctrl+s了

### 关于project module

project \<==\> workspace(eclipse)

module \<==\> project(eclipse)

module的删除

> open module settings -> 右键module delete

## 设置

### 设置背景图片

1. ctrl+shift+a
2. set background image
3. 选图片 搞定

## 快捷键

| 操作                        | 快捷键              | keymap searching |
|-----------------------------|---------------------|------------------|
| 全局搜索                    | 双击 Shift          |                  |
| 注释                        | Ctrl+/ Ctrl+Shift+/ |                  |
| 根据名称查找类或文件.       | ctrl+n              |                  |
| Navigating to Action        | ctrl+shift+a        |                  |
| 跳转到navigation bar(见图1) | alt+home            |                  |
| open doc                    | ctrl+q              | doc              |

图1

![图1](https://losssblog.oss-cn-hangzhou.aliyuncs.com/intellij-setting/1.png)

## snippet

| 操作 | 作用            |
|------|-----------------|
| psvm | generating main |
| sout | sysout          |

## 组合技

### create class without mouse

1. alt+f1
2. 1(project)
3. alt+insert

## 其他

### 目录结构说明

与eclipse不同 project 就相当于 workspace 在project中新建 module 就相当于eclipse中的 project

![](https://losssblog.oss-cn-hangzhou.aliyuncs.com/intellij-setting/1.png?x-oss-process=style/blogimage)

### 导入jar

1. 模块中新建 libs文件夹
2. 右击项目 open moudle setting
3. Dependencies
4. "+"sign choose 1JARs or directories
5. 选择搞定

## 参考

官方文档   https://www.jetbrains.com/help/idea/meet-intellij-idea.html
