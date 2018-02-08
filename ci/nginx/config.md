#### 开机自动启动

_vim /etc/init.d/nginx_ 添加以下网址中的脚本

[https://www.nginx.com/resources/wiki/start/topics/examples/redhatnginxinit/](https://www.nginx.com/resources/wiki/start/topics/examples/redhatnginxinit/)

{% em type="red" %}nginx=”/usr/sbin/nginx” 修改成nginx执行程序的路径。{% endem %}

{% em type="red" %}NGINX\_CONF\_FILE=”/etc/nginx/nginx.conf” 修改成配置文件的路径{% endem %}

  
修改权限

chmod a+x /etc/init.d/nginx

#### 防火墙配置

nginx防火墙 80端口

```
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
```

#### 配置nginx





