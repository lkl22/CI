#### Download

[http://nginx.org/en/download.html](http://nginx.org/en/download.html)

* 检查是否安装nginx

```
find -name nginx
```

* 安装需要的依赖

```
yum install gcc-c++ pcre pcre-devel zlib zlib-devel openssl openssl-devel
```

#### 安装nginx

```
tar -zxvf nginx-1.13.4.tar.gz
cd /developer/nginx-1.13.4/
./configure
make
make install
```

#### 启动nginx

```
whereis nginx
cd /usr/local/nginx/sbin/
./nginx
```





