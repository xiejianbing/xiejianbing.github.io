---
title: nginx
description: nginx的安装和使用
date: 2018-03-28 15:31:59
tags:
- nginx
---

### nginx安装

> 测试安装环境centOS6.8和centOS7,按照下面的步骤安装即可。

1、**安装依赖环境**

- gcc安装

安装 nginx 需要先将官网下载的源码进行编译，编译依赖 gcc 环境，如果没有 gcc 环境，则需要安装：

```
// yum install gcc-c++
yum -y install gcc gcc-c++ autoconf automake
```

- PCRE pcre-devel

> PCRE(Perl Compatible Regular Expressions) 是一个Perl库，包括 perl 兼容的正则表达式库。nginx 的 http 模块使用 pcre 来解析正则表达式，所以需要在 linux 上安装 pcre 库，pcre-devel 是使用 pcre 开发的一个二次开发库。nginx也需要此库
>
> ```
> yum install -y pcre pcre-devel
> ```

- zlib 安装

> zlib 库提供了很多种压缩和解压缩的方式， nginx 使用 zlib 对 http 包的内容进行 gzip ，所以需要在 Centos 上安装 zlib 库。

```
yum install -y zlib zlib-devel
```

- OpenSSL 安装

> OpenSSL 是一个强大的安全套接字层密码库，囊括主要的密码算法、常用的密钥和证书封装管理功能及 SSL 协议，并提供丰富的应用程序供测试或其它目的使用。
> nginx 不仅支持 http 协议，还支持 https（即在ssl协议上传输http），所以需要在 Centos 安装 OpenSSL 库。

```
yum install -y openssl openssl-devel
```

2、**安装nginx**

* 解压安装

```
// 解压
tar -zxvf  .tar.gz

./configure --prefix=/usr/local/nginx
make
make install
```

* 启动

```
/usr/local/nginx/sbin/nginx
```

> 修改配置文件后，需要先测试配置，然后再重启nginx

```
//测试配置文件是否有错误：
/usr/local/nginx/sbin/nginx  -t
//重启：
# /usr/local/nginx/sbin/nginx  -s stop
/usr/local/nginx/sbin/nginx  -s reload
```

### nginx 使用

未完待续……



