#### 配置字符集

```
vim /etc/my.cnf
```

\#默认字符集

\[mysqld\]

_default-character-set=utf8_

#### 配置防火墙

外部访问需开放3306端口

```
vim /etc/sysconfig/iptables
```

\#mysql port

_-A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT_

```
service iptables restart
```



