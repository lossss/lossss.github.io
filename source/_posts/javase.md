---
title: java
date: 2019-02-25 11:33:13
categories: java
tags: java
---

个人 javase 知识点杂谈,会有点长

<!--more-->

## DOS 知识

| 操作 | 操作     |
| ---- | -------- |
| cd   | 打开目录 |
| dir  | ls       |
| cls  | 清屏     |
| tab  | 自动补齐 |

## 数据类型

### 整型

```java
int a = 15;
int b = 015;//八进制
int c = 0x15;//16进制
int d = 0b1101;// 二进制
byte e = 127; //一个字节存储 -128~127
short //两个字节存储 -32768~32767
int //四个字节存储
long //八个字节存储
long globalPopulation = 74000000000L;
```

### 浮点型

```java
float a = 3.14F;//四个字节 精度小数点后7位
double b = 6.26;//八个字节 精度是float两倍

//浮点类型默认double
// 浮点型比较不精确 如果需要比较需要使用 BigDecimal类
float a = 0.1F;
double b = 1.0/10;
System.out.println(a == b);
// output false
BigDecimal a1 = new BigDecimal(1.0/10);
BigDecimal b1 = new BigDecimal(0.1);
System.out.println(a1.equals(b1));
```

### Tips

#### 基本数据类型转换

1.

#### 原码补码反码

```java
原码 00000001 =>1
    10000001 =>-1
补码 反码+1
反码 负数保留符号位其他位取反
0000 0110 =>6
1111 1001 =>-6
```

### 字符型

```java
char a ='A'; //两个字节 运算时可以当做整型处理
char b ='\t';
```

## 数组

```java
//拷贝方法
/**
 * @param      src      the source array.
 * @param      srcPos   starting position in the source array.
 * @param      dest     the destination array.
 * @param      destPos  starting position in the destination data.
 * @param      length   the number of array elements to be copied.
*/
System.arraycopy(src, srcPos, dest, destPos, length);
```

## 内部类

```java
public class Outer {
	public static void main(String[] args) {
		Face f = new Face();
		Face.Nose n = f.new Nose();
		n.breath();
		Face.Ear e = new Face.Ear();
		e.listen();
	}
}

class Face {
	int type;
	String shape="瓜子脸";
	static String color="红润";

	class Nose {

		void breath(){
			System.out.println(shape);
			System.out.println(Face.this.type);
			System.out.println("呼吸！");
		}
	}

	static class Ear {
		void listen(){
			System.out.println(color);
			System.out.println("我在听！");
		}
	}

}
```

## 垃圾回收机制
