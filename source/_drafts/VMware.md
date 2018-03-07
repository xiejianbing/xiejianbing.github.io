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

