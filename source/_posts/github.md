---
title: Github
date: 2017-12-28 15:31:03
description: github相关配置
tags:
  - github
---

# Github SSH配置

* 创建密钥

  ```
  $ ssh-keygen -t rsa -C "xiejb@163.com"
  ```

  > 密匙的创建方式有多种，此处是通过命令创建 ，三次回车，即可设置密码为空

* 将生成的id_rsa.pub文件 (在目录C:\Users\Administrator.ssh) 内容添加到github上,登录github设置即可

  {% asset_img ssh_key.jpg %}


