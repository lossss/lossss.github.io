---
title: python-1
date: 2017-08-09 00:40:03
categories: python
tags: python
---
python 第一天的一些练习
<!--more-->
``` python

val = input("请输入温度(例:32C)")
if val[-1] in ["C", "c"]:
    f = 1.8*float(val[0:-1])+32
    print("转换后的温度为：%.2fF" % f)
elif val[-1] in ["F", "f"]:
    c = (float(val[0:-1])-32)/1.8
    print("转换后的温度为：%.2fC" % c)
else:
    print("输入有误")


# 字符串拼接
str1 = input('请输入一个人的名字: ')
str2 = input('请输入一个国家的名字: ')
print("世界这么大,{} 想去{} 看看".format(str1, str2))

# 整数序列求和
n = input("请输入整数N")
sum = 0
for i in range(int(n)):
    sum += i + 1
print("1到N求和结果:", sum)

# 九九乘法表
for i in range(1, 10):
    for j in range(1, i+1):
        sum += i + 1
print("1到N求和的结果为", sum)

# 九九乘法表
for i in range(1, 10):
    for j in range(1, i+1):
        sum += i + 1
print("1到N求和的结果为", sum)
```
