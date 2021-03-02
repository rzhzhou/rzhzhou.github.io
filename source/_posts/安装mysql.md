---
title: 安装mysql
date: 2019-08-02 14:51:14
tags: 'Mysql'
---

安装Mysql
--------
在子系统中执行以下命令安装`Mysql`
```
sudo apt install mysql-server
```

安装成功之后无法进入mysql，需要修改密码，如下操作：
1.进入`/etc/mysql/`目录，并用root权限打开debian.cnf文件

```
cd /etc/mysql
sudo vim debian.cnf
```

2.先启动mysql服务，使用这个文件中的用户名和密码进入mysql
```
mysql -u debian-sys-maint -p
```

3.然后修改密码为`123456`
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
```


卸载mysql
--------

先杀死mysql进程，然后再进行下面步骤。
```
sudo apt-get autoremove mysql* --purge      //步骤一
sudo apt-get remove apparmor    //步骤二
dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P   //清除残留数据
```

如果安装mysql 无限卡死 比如安装到90%以上不动，请取消当前操作（ctrl + z），卸载mysql的依赖包，在安装
