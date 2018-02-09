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

#### Nginx代理设置

_vim /usr/local/nginx/conf/vhost/gerrit.conf_

```
server {
    listen *:8088; //监听的端口
    server_name gerrit.wenbin.com;
    allow   all;
    deny    all;

    auth_basic "Welcomme to Gerrit Code Review Site!";
    auth_basic_user_file /home/gerrit/gerrit_site/htpasswd.conf; //AuthUserFile路径，即http认证文件

    location / {
        proxy_pass  http://127.0.0.1:8081; //代理到本地的8081端口，对应于gerrit的监听端口
        proxy_set_header X-Forwarded-For $remote_addr;
        proxy_set_header Host $host;
    }

    error_page  404   /404.html;
    location = /404.html {

    }

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   html;
    }
}
```



