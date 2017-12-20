---
layout:     post
title:      升级phpStudy的MySQL
subtitle:   升级phpStudy的MySQL
date:       2017-12-19
author:     BY lijunxian
header-img: img/post-bg-debug.png
catalog: true
tags:
    - PHP
    - MySQL
    - Magento
---

> 下载了magento2,发现要mysql5.6以上，本地phpstudy的mysql是5.5，需要升级

## 备份原有mysql目录

首先我们需要备份原有目录，防止mysql升级失败

## 下载MySQL5.6

- 前往下载，[https://www.mysql.com/downloads/](https://www.mysql.com/downloads/)

## 升级

- 解压压缩包，覆盖phpstudy安装目录下原有mysql目录中文件
- 复制 my-default.ini ，重命名为 my.ini
- 打开 my.ini，找到 #basedir 处编辑：
 
```
 basedir=D:/phpStudy/MySQL
 datadir=D:/phpStudy/MySQL/data
```
- 将mysql中斌目录添加至环境变量


## 安装服务
```
mysqld -install
```

## 启动服务
```
net start MySQL
```

## 登陆
```
C:\Users\dell>mysql -uroot -p
Enter password: ****
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```
>此时可能会报错，要求输入密码（新安装的数据库可空密码登陆）

## 更改密码
- 打开 my.ini，找到 [mysqld]，在下面添加：`skip-grant-tables`,
此时使用 root 账号，密码处按回车即可登录。
- 修改密码并刷新权限
```
mysql>update mysql.user set authentication_string=password('new_password') where user='root' and Host ='localhost'
mysql> ALTER USER USER() IDENTIFIED BY 'news_password';
```
- 注释掉 my.ini 中刚才添加的`skip-grant-tables`
- 重新登陆即可