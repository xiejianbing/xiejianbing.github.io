---
title: Maven
description: Maven的安装和使用
date: 2018-03-21 14:18:24
tags:
  - maven
---

## 1.简介

```

```

## 2.作用


> 帮助下载jar、寻找依赖，帮助下载依赖、热部署（应用正在运行时升级引用，不需要重启）、
清理、编译、测试、报告、打包、部署，模块化管理


## 3.下载和安装

> 安装maven之前 需要确认正确安装了jdk

**windows下下载安装**

* 下载

  ​     下载地址`http://maven.apache.org/download.cgi `  [ 点击下载](http://maven.apache.org/download.cgi )  ,下载后解压到指定位置

* 环境配置

> 环境变量中配置JAVA_HOME = D:\Program Files\Java\jdk1.8.0_112
> 环境变量 path 加  D:\Program Files\apache-maven\bin（maven解压后的路径）

**Linux下下载安装**

* 创建一个文件夹  进入目录  

``` 
mkdir /usr/local/maven
cd /usr/local/maven
```

* 下载maven的tar包

  ````
  wget http://mirrors.hust.edu.cn/apache/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz
  ````

* 解压tar

  ```
  tar -xvf apache-maven-3.5.2-bin.tar.gz 
  ```

* 配置环境

     ```
     //打开环境变量的配置文件
     vim /etc/profile
     ```

//新增行MAVEN_HOME,等于号后面是maven解压的文件夹地址
export MAVEN_HOME=/usr/local/maven/apache-maven-3.5.2
//找到PATH行,追加$MAVEN_HOME/bin
例如
PATH=`$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH`
//重新刷新配置文件
source /etc/profile
     ```

* 测试

```
mvn -version
```






## 4.验证结果

验证配置结果：
```
mvn -v
```

{% asset_img version.jpg %}



## 5.配置


> 指定本地仓库：
 改D:\Program Files\apache-maven\conf\setting.xml文件


## 6.Maven的约定

```
src/main/java :存放项目的java文件
src/main/resources:存放项目的资源文件，如springMVC等的配置文件
src/test/java :存放所有的测试的java文件
src/test/resources:存放测试用的资源文件
target ：项目输出位置
pom.xml :构建文件

```

## 7.Maven的常用命令

```
 mvn complie 编译
 mvn clean  清理
 mvn test 测试
 mvn package 打包
 mvn install 把打出的包装载到本地仓库
```

## 8.Maven坐标

## 9.依赖

## 10.仓库

## 11.Maven的生命周期和插件

------

# Maven常用命令

## 1. 安装jar到本地仓库

```
mvn install:install-file -DgroupId=com.oracle -DartifactId=ojdbc14 -Dversion=10.2.0.4.0 -Dpackaging=jar -Dfile=ojdbc6.jar
```