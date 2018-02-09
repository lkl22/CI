#### Install

```
yum -y install gitweb
```

#### Config

_vim /etc/gitweb.conf_

```markdown
# Set the path to git projects.  This is an absolute filesystem path which will
# be prepended to the project path.
#our $projectroot = "/var/lib/git";
$projectroot = "/home/gerrit/gerrit_site/git";  #插入一行，指定gerrit里git仓库的所在位置
```

#### 代理设置

* apache

_vim /etc/httpd/conf.d/gitweb.conf_

```markdown
#
# gitweb
#
Alias /gitweb "/var/www/git"
<Directory "/var/www/git">
    Options +ExecCGI
    AddHandler cgi-script .cgi
    DirectoryIndex index.cgi gitweb.cgi
    Order allow,deny
    Allow from all
</Directory>
```



