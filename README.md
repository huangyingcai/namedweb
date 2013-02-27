namedmanager
##########


###1.简介
NamedManager 是一个基于 Web 的 DNS 管理系统，可用来添加、调整和删除 DNS 的 zones/records 数据，支持 Bind 作为后端的 DNS 服务，支持 IPv4 和 IPv6。

###2.用途
最简单直接的用途是在管理DNS记录上。添加删除更方便

![Alt text](img/first.png "前台管理截图")

####3.安装和使用

**本文是针对centos 6 系统为范本**

下载包并安装。rpm包在rpm目录

安装如下：

	rpm -Uvh namedmanager-bind-1.5.1-1.el6.noarch.rpm
	[root@localhost noarch]# rpm -ihv namedmanager-www-1.5.1-1.el6.noarch.rpm 
	Preparing...                ########################################### [100%]
	   1:namedmanager-www       ########################################### [100%]
	   Reloading httpd...
	   Reloading httpd: 
	   Run cd /usr/share/namedmanager/resources/; ./autoinstall.pl to install the SQL database.

![Alt text](img/importsql.png "导入sql语名")
    
安装数据库

	yum -y install mysql-server

启动Mysql

	service mysqld start

设置mysql密码

	mysqladmin -u root password '123456

namedmanager配置文件如下：

	/etc/namedmanager/config.php

	<?php
	$config["db_host"] = "localhost";                       // hostname of the MySQL server
	$config["db_name"] = "myapp";                           // database name
	$config["db_user"] = "root";                            // MySQL user
	$config["db_pass"] = "";                                // MySQL password (if any)
	$config["AUTH_METHOD"] = "sql";
	?>

更改密码为mysql的密码	

####参考文档

官方安装手册

<https://projects.jethrocarr.com/p/oss-namedmanager/page/Installation-RPM/>
