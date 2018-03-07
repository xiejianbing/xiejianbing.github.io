---
title: redis
description: redis的安装和简单使用
date: 2018-03-07 10:22:46
tags:
- redis
---

### Linux下下载安装

```
$ wget http://download.redis.io/releases/redis-4.0.8.tar.gz
$ tar -zxvf redis-4.0.8.tar.gz (解压后将文件移动到制定目录 如：（/usr/local/redis)
$ cd redis-4.0.8
$ make
```

> make: cc: Command not found make: *** [adlist.o] Error 127
>
> 新安装的Linux系统没有安装gcc环境，需要安装gcc
>
>  `yum  install  gcc-c++`

启动：

```
$ cd src
$ ./redis-server
```

注意这种方式启动redis 使用的是默认配置。也可以通过启动参数告诉redis使用指定配置文件使用下面命令启动。

```
$ cd src
$ ./redis-server redis.conf
```

edis.conf是一个默认的配置文件。我们可以根据需要使用自己的配置文件。

启动redis服务进程后，就可以使用测试客户端程序redis-cli和redis服务交互了。 比如：

```
$ cd src
$ ./redis-cli
redis> set foo bar
OK
redis> get foo
"bar"
```

### 设置redis开机启动

1、设置redis.conf中daemonize为yes,确保守护进程开启,也就是在后台可以运行

2、拷贝 redis 安装目前下的 /usr/local/redis/utils/redis_init_script 到 /etc/init.d/redis文件中；

````
cp /usr/local/redis/utils/redis_init_script /etc/init.d/redis
````

3、修改/etc/init.d/redis 文件（拷贝后的文件）。修改redis安装的相关文件安装目录

```
#!/bin/sh

# chkconfig: 2345 10 90  
# description: Start and Stop redis

# Simple Redis init.d script conceived to work on Linux systems
# as it does use of the /proc filesystem.

REDISPORT=6379
EXEC=/usr/local/redis/src/redis-server
CLIEXEC=/usr/local/redis/src/redis-cli

PIDFILE=/var/run/redis_${REDISPORT}.pid
#CONF="/etc/redis/${REDISPORT}.conf"
CONF="/usr/local/redis/redis.conf"
```

> 必须把下面两行注释放在/etc/init.d/redis文件靠前的注释中：否则chkconfig redis on命令失败

```
# chkconfig: 2345 10 90  
# description: Start and Stop redis
```

4、开机启动设置，执行一下命令：

- 添加redis服务：

```
chkconfig --add redis
```

- 设为开机启动 ：

```
chkconfig redis on
```

- 打开redis命令:

```
service redis start
```

- 关闭redis命令:

```
service redis stop
```

5、重启动检查 
init 6

```
ps -ef|grep redis
```