---
title: java
date: 2019-02-25 11:33:13
categories: java
tags: java
---
个人java知识点笔记
<!--more-->


# DOS 知识
| 操作 | 操作     |
|------|----------|
| cd   | 打开目录 |
| dir  | ls       |
| cls  | 清屏     |
| tab  | 自动补齐 |

# 数据类型
## 整型
```java
int a = 15;
int b = 015;//八进制
int c = 0x15;//16进制
int d = 0b1101;// 二进制

long globalPopulation = 74000000000L;
```

## 浮点型
```java
float a = 3.14F;
double b = 6.26;

// 浮点型比较不精确 如果需要比较需要使用 BigDecimal类
float a = 0.1F;
double b = 1.0/10;
System.out.println(a == b);
// output false
// 
BigDecimal a1 = new BigDecimal(1.0/10);
BigDecimal b1 = new BigDecimal(0.1);
System.out.println(a1.equals(b1));
```
##
```java
