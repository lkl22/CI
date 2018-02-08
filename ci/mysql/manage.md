* root用户登录

```
mysql -u root
mysql -u root -p //使用密码登录
```

* 添加一个用户

```
insert into mysql.user(Host,User,Password) values("localhost","userName",password("pwd"));
```

* 删除匿名用户

```
delete from mysql.user where user='';
```

* 设置密码

```
set password for root@localhost=password('root');
set password for root@127.0.0.1=password('root');
```



* 查看用户表

```
select user,host,password from mysql.user;
```

_\G代表格式化_

```
select * from mysql.user\G;
```

* 显示数据库

```
show databases;
```

* 使用数据库

```
use databaseName
```

* 创建数据库databaseName

    create database `databaseName` default character set utf8 collate utf8_general_ci;

* 删除数据库

```
drop database 'databaseName';
```

* 修改数据库权限

```
grant all privileges on databaseName.* to userName@'%' identified by 'userName' with grant option;
```

* 刷新权限

```
flush privileges;
```



