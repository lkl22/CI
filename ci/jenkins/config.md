#### 修改端口

_vim /etc/sysconfig/jenkins_

```markdown
## Type:        integer(0:65535)
## Default:     8080
## ServiceRestart: jenkins
#
# Port Jenkins is listening on.
# Set to -1 to disable
#
JENKINS_PORT="8089"  //将默认8080端口改为8089
```

vim /etc/passwd将false改为bash，否则无法切换到jenkins账户，ssh-keygen就无法生成密钥了

```markdown
jenkins:x:996:994:Jenkins Continuous Integration Server:/var/lib/jenkins:/bin/false -> bash
```



