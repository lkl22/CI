#### 添加新的账户

1、在认证文件所在的目录，执行下面的指令创建新的用户

```
[root@centos233 gerrit_site]# htpasswd -m htpasswd.conf newUser
New password: 
Re-type new password: 
Adding password for user newUser
```

2、在网页上登录

第一次使用登录的第一个用户为管理员

![](/assets/gerrit_login.png)

#### 注册邮箱

![](/assets/gerrit_register_email.png)

![](/assets/gerrit_email_verification.png)

#### Group管理

* 创建用户组

![](/assets/gerrit_group_create.png)

* 管理用户组成员

![](/assets/gerrit_group_members.png)

















