#### 默认安装

```
rpm -i https://gerritforge.com/gerritforge-repo-1-2.noarch.rpm
yum install -y gerrit
```

#### war包安装

* Download

wget [https://gerrit-releases.storage.googleapis.com/gerrit-2.14.3.war](https://gerrit-releases.storage.googleapis.com/gerrit-2.15-rc2.war)

* 添加user

```
useradd gerrit
cd /home/gerrit/
su gerrit  //切换用户
```

* 创建数据库

```
mysql -u gerrit -p  //使用gerrit用户登录
create database gerritdb default character set utf8 collate utf8_general_ci;
grant all privileges on gerritdb.* to gerrit@'localhost' identified by 'gerrit' with grant option;
flush privileges;
```

* 指令安装

在war包所在目录下，执行**java -jar gerrit\*.war init -d ~/gerrit\_site**，-d 后跟安装目录

```
[gerrit@centos233 ~]$ java -jar gerrit*.war init -d ~/gerrit_site
Using secure store: com.google.gerrit.server.securestore.DefaultSecureStore
[2018-02-08 18:20:49,823] [main] INFO  com.google.gerrit.server.config.GerritServerConfigProvider : No /home/gerrit/gerrit_site/etc/gerrit.config; assuming defaults

*** Gerrit Code Review 2.14.3
*** 

Create '/home/gerrit/gerrit_site' [Y/n]? y

*** Git Repositories
*** 

Location of Git repositories   [git]:  这里一定要写git放的目录，没有的话自己会创建的

*** SQL Database
*** 

Database server type           [h2]: mysql  使用的数据库类型

Gerrit Code Review is not shipped with MySQL Connector/J 5.1.41
**  This library is required for your configuration. **
Download and install it now [Y/n]? y
Downloading https://repo1.maven.org/maven2/mysql/mysql-connector-java/5.1.41/mysql-connector-java-5.1.41.jar ... OK
Checksum mysql-connector-java-5.1.41.jar OK
Server hostname                [localhost]: 
Server port                    [(mysql default)]: 
Database name                  [reviewdb]: gerritdb
Database username              [gerrit]: 
gerrit's password              : 
              confirm password : 

*** Index
*** 

Type                           [LUCENE/?]:  默认就好，直接回车

*** User Authentication
*** 

Authentication method          [OPENID/?]: http 一定要写http，不然就不是反向代理了，写development_become_any_account就随意登陆了
Get username from custom HTTP header [y/N]? n 一定要n，不然反向代理gerrit报错为缺少一个y的header
SSO logout URL                 : 
Enable signed push support     [y/N]? n

*** Review Labels
*** 

Install Verified label         [y/N]? y

*** Email Delivery
*** 

SMTP server hostname           [localhost]: smtp.163.com
SMTP server port               [(default)]: 25  25端口是163的smtp
SMTP encryption                [NONE/?]: 
SMTP username                  [gerrit]: xxx@163.com
sz.lkl@163.com's password      : 
              confirm password : 

*** Container Process
*** 

Run as                         [gerrit]:  这是用户，root也可以
Java runtime                   [/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.102-4.b14.el7.x86_64/jre]: 
Copy gerrit-2.14.3.war to /home/gerrit/gerrit_site/bin/gerrit.war [Y/n]? y
Copying gerrit-2.14.3.war to /home/gerrit/gerrit_site/bin/gerrit.war

*** SSH Daemon
*** 

Listen on address              [*]: 
Listen on port                 [29418]: 
Generating SSH host key ... rsa... dsa... ed25519... ecdsa 256... ecdsa 384... ecdsa 521... done

*** HTTP Daemon
*** 

Behind reverse proxy           [y/N]? y
Proxy uses SSL (https://)      [y/N]? n
Subdirectory on proxy server   [/]: 
Listen on address              [*]: 127.0.0.1
Listen on port                 [8081]: 
Canonical URL                  [http://*/]: http://gerrit.wenbin.com

*** Cache
*** 


*** Plugins
*** 

Installing plugins.
Install plugin commit-message-length-validator version v2.14.3 [y/N]? y
Installed commit-message-length-validator v2.14.3
Install plugin download-commands version v2.14.3 [y/N]? y
Installed download-commands v2.14.3
Install plugin hooks version v2.14.3 [y/N]? y
Installed hooks v2.14.3
Install plugin replication version v2.14.3 [y/N]? y
Installed replication v2.14.3
Install plugin reviewnotes version v2.14.3 [y/N]? y
Installed reviewnotes v2.14.3
Install plugin singleusergroup version v2.14.3 [y/N]? y
Installed singleusergroup v2.14.3
Initializing plugins.

Initialized /home/gerrit/gerrit_site
Executing /home/gerrit/gerrit_site/bin/gerrit.sh start
Starting Gerrit Code Review: OK
Waiting for server on gerrit.wenbin.com:80 ... OK
Opening http://gerrit.wenbin.com/#/admin/projects/ ...OK
[gerrit@centos233 ~]$
```

vim gerrit\_site/etc/gerrit.config

