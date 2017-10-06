---
title: maven-notes
date: 2017-09-24 16:19:41
categories: maven
tags: maven
---
maven笔记
<!--more-->
使用教程 慕课 http://www.imooc.com/learn/443

配置参数说明
```
groupId //com.eurus.maven03
artifacted //maven03-service
version  //1.0.0SPANSHOT
package //com.eurus.maven03.service
```
maven常用命令

```
mvn -v  查看版本
mvn compile 编译
mvn test 测试
mvn package 打包
mvn clean 删除target
mvn install
```
创建目录的方式
1. archetype:generate 按照提示进行选择
2. archetype:gennerate -DgroupId=组织名,公司网址反写+项目名
                       -DartifactId=项目名-模块名
                       -Dversion=版本号
                       -Dpackage=代码所存在的包名

可以参考junit的写法
``` xml
<dependency>
  <groupId>org.apache.directory.junit</groupId>
  <artifactId>junit-addons</artifactId>
  <version>0.1</version>
</dependency>
```

国内使用阿里的镜像
``` xml
<mirror>
          <id>alimaven</id>
          <mirrorOf>central</mirrorOf>
          <name>aliyun maven</name>
          <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
</mirror>
```
