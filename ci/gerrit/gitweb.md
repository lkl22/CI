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



