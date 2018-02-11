官网：[https://jenkins.io/doc/book/installing/](https://jenkins.io/doc/book/installing/)

安装包：[https://pkg.jenkins.io/](https://pkg.jenkins.io/)

根据操作系统选择不同的pkg，这里选择的是[https://pkg.jenkins.io/redhat/](https://pkg.jenkins.io/redhat/)

```
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key

yum install jenkins

或者
下载rpm安装包，使用rpm安装
rpm -ivh jenkins-2.7.4-1.1.noarch.rpm
```

This package installation will:

* Setup Jenkins as a daemon launched on start. See`/etc/init.d/jenkins`for more details.

* Create a_`jenkins`_user to run this service.

* Direct console log output to the file`/var/log/jenkins/jenkins.log`. Check this file if you are troubleshooting Jenkins.

* Populate`/etc/default/jenkins`with configuration parameters for the launch, e.g`JENKINS_HOME`

* Set Jenkins to listen on port 8080. Access this port with your browser to start configuration.



