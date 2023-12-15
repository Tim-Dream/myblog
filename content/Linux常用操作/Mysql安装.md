---
title: "MySql安装"
date: 2023-12-14T20:19:07+08:00
draft: false
---

* 安装
``` shell
yum -y install mysql80-community-release-el7-7.noarch.rpm
yum -y install mysql-community-server
systemctl start mysqld.service
```

* 初始化root密码
``` shell
grep 'password' /var/log/mysqld.log
mysql -u root -p
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
```

* 新建用户
``` shell
CREATE USER 'dream'@'%' IDENTIFIED BY 'cmbjxCCWTN008#';
GRANT CREATE,ALTER,DELETE,INSERT,SELECT ON *.* TO 'dream'@'%';
GRANT ALL ON *.* TO 'dream'@'%';
flush privileges;
```

* 查询用户权限
``` shell
select user,host from mysql.user;
```

* 修改用户请求
``` shell
update mysql.user set host='%' where user='root';
```
