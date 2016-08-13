---
layout:            post
title:             "Vagrant Notes"
menutitle:         "Vagrant Notes"
category:          Notes
author:            LabbyY
tags:              note
cover:             /media/img/universe1.jpg
---


## Install Vagrant

## Use Vagrant

 - vagrant up 时 outprint 的以下信息表示了 共享目录的 host 路径及 vm 路径：

  `==> default: Mounting shared folders...`

 `default: /vagrant => /Users/xiaoxue/Desktop/ninghao-project`

- 要配置共享目录，在Vagrantfile中查找以下项并修改：

    `config.vm.synced_folder "host路径（以vagrantfile所在目录为根目录）", "虚拟路径"`
