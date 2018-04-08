---
title: VMware
description: VMware基本设置
tags:
  - VMware
---

## centOS安装 VMware Tools

* 启动CentOS虚拟机

  虚拟机》》安装VMware Tools

* 创建挂载点目录

  ` mkdir /mnt/cdrom`

* 挂载光驱

  `mount /dev/cdrom /mnt/cdrom`

  > 可能会出现mount: block device /dev/sr0 is write-protected, mounting read-only

  解决办法：

  `mount -o ro /dev/cdrom /mnt/cdrom`

* 查看挂载结果

  `cd /mnt/cdrom`

  ls查看/mnt/cdrom路径下的文件信息，发现有一个VMware-Linux-tools.tar.gz文件说明挂在成功

* 5 解压缩文件到/tmp

  tar -zxvf /mnt/cdrom/vmware-linux-tools.tar.gz -C /tmp

* 进入解压后的目录

  cd /tmp/vmware-tools-distrib路径下

* 执行./vmware-install.pl文件

  `./vmware-install.pl`

* 8、在安装过中如果发现无法运行说明你的CentOS系统缺少Perl环境，此时你需要先安装perl

  `yum install perl`




* centos6.8 网络配置

1. 查看默认配置（默认eth0是禁用的） 
   ifconfig -a
2. 编辑网卡配置文件 
   vi /etc/sysconfig/network-scripts/ifcfg-eth0 
   注：eth0只是我的网卡名，你的可能不叫这个，所以认住这个ifcfg-开头（后面默认网卡名）就行

按i键开始进行配置

要修改的内容：
标识 5 ONBOOT=no 修改为 ONBOOT=yes 

是否随系统启动

标识 7 BOOTPROTO=dhcp 修改为 BOOTPROTO=static 

IP地址分配方式，是DHCP服务器自动分配，还是手动配置

要增加的内容：
 IPADDR=192.168.1.108 << IP
 NETMASK=255.255.255.0 << 子网掩码
 GATEWAY=192.168.1.1 <<网关
 DNS1=202.96.128.166
 DNS2=202.96.134.133
 DNS配置根据当地网络供应商进行添加



1. 退出保存 
   ①按Esc键 
   ②输入:wq回车
2. 重启网络服务： 
   service network restart