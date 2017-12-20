---
layout:     post
title:      phpstudy安装magento2的问题
subtitle:   phpstudy安装magento2的问题
date:       2017-12-19
author:     BY lijunxian
header-img: img/post-bg-debug.png
catalog: true
tags:
    - PHP
    - Magento
---

> 长话短说，直入正题

## php版本
> magento2需要**php7.0**以上部分版本，具体参考官网说明

## php扩展
>php需要打开**soap**和**intl**扩展，在打开该扩展时，可能php会报错，提示icc*.dll不存在，此时需要下载所需dll文件，放在所切换的php版本根目录下

## composer
>magento2需要composer才能运行，此时在命令行中将目录切换至php根目录，前往[composer中文镜像站](https://pkg.phpcomposer.com/)按流程使用命令行下载安装，然后将composer.phar复制到magento2目录下。
配置composer镜像地址为国内
`composer config -g repo.packagist composer https://packagist.phpcomposer.com`
然后执行
`composer install`

## 安装报错处理
- 在安装magento时在install阶段可能会报错，点击try again即可正常安装（不知道原因）