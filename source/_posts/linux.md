---
title: linux命令
description: Linux命令大全
date: 2018-03-06 09:52:46
tags:
- linux
- 命令
---

### Wget (网络文件下载)

> **wget命令**用来从指定的URL下载文件

安装 `yum install wget` [参考](http://man.linuxde.net/wget)

### pwd (显示路径)

显示当前所处的路径。

### export

​     用于将shell变量输出为环境变量，或者将shell函数输出为环境变量。

### mkdir (创建)

* mkdir -p  /user/local/test

>   -m, --mode=模式   设定权限<模式> (类似 chmod)，而不是 rwxrwxrwx 减 umask
>   -p, --parents     需要时创建上层目录，如目录早已存在则不当作错误
>   -v, --verbose     每次创建新目录都显示信息
>   -Z, --context=CONTEXT (SELinux) set security context to CONTEXT
>       --help     显示此帮助信息并退出
>       --version  输出版本信息并退出



### netstat & nmap (端口号查看)

* 安装

> yum install net-tools
>
> yum install nmap



* netstat 命令

  `netstat -anlp | grep 22`

> - -a (all)显示所有选项，默认不显示LISTEN相关
> - -t (tcp)仅显示tcp相关选项
> - -u (udp)仅显示udp相关选项
> - -n 拒绝显示别名，能显示数字的全部转化成数字。
> - -l 仅列出有在 Listen (监听) 的服務状态
> - -p 显示建立相关链接的程序名
> - -r 显示路由信息，路由表
> - -e 显示扩展信息，例如uid等
> - -s 按各个协议进行统计
> - -c 每隔一个固定时间，执行该netstat命令。
>
> 提示：LISTEN和LISTENING的状态只有用-a或者-l才能看到



* nmap

> nmap  127.0.0.1

