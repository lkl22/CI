#### http的认证文件

* 安装工具包

```
yum install -y httpd-tools
```

* 创建用户、密码

**htpasswd -c htpasswd.conf admin**在当前目录创建 _**htpasswd.conf **_文件，并添加一个admin用户并设置密码

```
[gerrit@centos233 gerrit_site]$ htpasswd -c htpasswd.conf admin
New password: 
Re-type new password: 
Adding password for user admin
```

* 新增用户、修改用户密码

htpasswd -m htpasswd.conf admin

```
[gerrit@centos233 gerrit_site]$ htpasswd -m htpasswd.conf userName
New password: 
Re-type new password: 
Adding password for user userName
```



