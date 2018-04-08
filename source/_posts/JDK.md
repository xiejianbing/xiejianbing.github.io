---
title: JDK
description: JDK安装和环境配置
date: 2018-03-27 17:24:14
tags:
 - JDK
 - centOS 
---



# centOS  JDK 环境配置

[TOC]

## JDK安装

### 方法一：手动解压JDK的压缩包，然后设置环境变量

**1. 在/usr/目录下创建java目录**

```
mkdir/usr/java

// cd /usr/java
```

**2. 下载jdk,然后解压**

*  官网下载 上传到服务器
*  命令行下载

```
 curl -O http://download.Oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.tar.gz 
 
// http://download.oracle.com/otn-pub/java/jdk/8u112-b15/jdk-8u112-linux-i586.tar.gz
```

 * 解压

```
 tar -zxvf  jdk-7u80-linux-x64.tar.gz 
```

**3. 设置环境变量**

```
vi /etc/profile
```

* 在profile中添加如下内容:

```
JAVA_HOME=/usr/local/java/jdk1.8.0_131
JRE_HOME=/usr/local/java/jdk1.8.0_131/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```
*  让修改生效:

```
 source /etc/profile
```
**4 .验证JDK有效性**

```
[root@localhost java]# java -version
java version "1.7.0_79"
Java(TM) SE Runtime Environment (build 1.7.0_79-b15)
Java HotSpot(TM) 64-Bit Server VM (build 24.79-b02, mixed mode)
```

### 方法二：用yum安装JDK

> 这种方式只能安装openjdk  建议使用另外两种方式安装sunJDK 

**1. 查看yum库中都有哪些jdk版本(暂时只发现了openjdk)**

```
[root@localhost ~]# yum search java|grep jdk

[root@localhost ~]# yum search java-1.8

[root@localhost ~]# yum -y list java*
```

**2. 选择版本,进行安装**

* jre环境

```
[root@localhost ~]# yum install java-1.8.0-openjdk
```
*  开发环境（编译环境 javac）

```
yum -y install java-1.8.0-openjdk-devel.x86_64
```

> 安装完之后，默认的安装目录是在: /usr/lib/jvm/

**3. 设置环境变量**

    同上

### 方法三：用rpm安装JDK
### 方法三：用rpm安装JDK
### 方法三：用rpm安装JDK

**1.下载rpm安装文件**

```
[root@localhost ~]$ curl -O http://download.oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.rpm
```

**2. 使用rpm命令安装**

```
[root@localhost  ~]# rpm -ivh jdk-7u79-linux-x64.rpm
```

> 注:和yum安装类似，不用设置环境变量就可以运行java命令。rpm安装方式默认会把jdk安装到/usr/java/jdk1.7.0_79，然后通过三层链接，链接到/usr/bin,具体链接如下：

```
[root@localhost ~]# cd /bin
[root@localhost bin]# ll|grep java
lrwxrwxrwx. 1 root root    25 Mar 28 11:24 jar ->/usr/java/default/bin/jar
lrwxrwxrwx. 1 root root    26 Mar 28 11:24 java -> /usr/java/default/bin/java
lrwxrwxrwx. 1 root root    27 Mar 28 11:24 javac ->/usr/java/default/bin/javac
lrwxrwxrwx. 1 root root    29 Mar 28 11:24 javadoc ->/usr/java/default/bin/javadoc
lrwxrwxrwx. 1 root root    28 Mar 28 11:24 javaws ->/usr/java/default/bin/javaws
lrwxrwxrwx. 1 root root    30 Mar 28 11:24 jcontrol ->/usr/java/default/bin/jcontrol
[root@localhost bin]# cd /usr/java/
[root@localhost java]# ll
total 4
lrwxrwxrwx. 1 root root  16 Mar 28 11:24 default-> /usr/java/latest
drwxr-xr-x. 8 root root 4096 Mar 28 11:24 jdk1.7.0_79
lrwxrwxrwx. 1 root root  21 Mar 28 11:24 latest -> /usr/java/jdk1.7.0_79
```
### 方法四：Ubuntu 上使用apt-get安装JDK

**1.查看apt库都有哪些jdk版本**

```
root@linuxidc:~# apt-cache search java|grep jdk
```

**2.选择版本进行安装**

```
root@linuxidc:~# apt-get install openjdk-7-jdk
```




## 查看JDK安装路径

* 方法1

> 使用`$JAVA_HOME` 的话能定位JDK的安装路径的前提是配置了环境变量`$JAVA_HOME`，否则如下所示，根本定位不到JDK的安装路径

```
echo $JAVA_HOME
```
* 方法2

```
[root@iZ2ze2wsgz4pbqal9up37yZ jvm]# java -version
openjdk version "1.8.0_141"
OpenJDK Runtime Environment (build 1.8.0_141-b16)
OpenJDK 64-Bit Server VM (build 25.141-b16, mixed mode)
[root@iZ2ze2wsgz4pbqal9up37yZ jvm]# which java
/usr/bin/java
[root@iZ2ze2wsgz4pbqal9up37yZ jvm]# ls -lrt /usr/bin/java 
lrwxrwxrwx 1 root root 22 Aug 21 16:18 /usr/bin/java -> /etc/alternatives/java
[root@iZ2ze2wsgz4pbqal9up37yZ jvm]# ls -lrt /etc/alternatives/java
lrwxrwxrwx 1 root root 73 Aug 21 16:18 /etc/alternatives/java -> /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.141-1.b16.el7_3.x86_64/jre/bin/java
[root@iZ2ze2wsgz4pbqal9up37yZ jvm]#
```

```
JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.141-1.b16.el7_3.x86_64
JRE_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.141-1.b16.el7_3.x86_64/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```
## 卸载

* 查看是否安装

```
yum list installed |grep java  
```

* yum卸载

```
[root@192 ~]# yum -y remove java-1.8.0-openjdk*        *表时卸载所有openjdk相关文件输入  
[root@192 ~]# yum -y remove tzdata-java.noarch         卸载tzdata-java  
```
* rpm卸载

```
  查看版本：rpm -qa|grep jdk
  
  卸载：rpm -e  --nodeps  jdk-1.6.0_10-fcs
``
```