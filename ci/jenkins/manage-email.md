### 一、Jenkins内置默认的邮件通知配置

1、全局配置

**Jenkins -&gt; Manage Jenkins -&gt; Configure System**

系统管理员的邮箱配置![](/assets/jenkins/jenkins_email_admin_address.png)邮件通知项，填入SMTP服务器信息及用户名、密码等认证信息。

![](/assets/jenkins/jenkins_global_email_notification.png)

在测试接收邮箱会收到由Jenkins系统管理员的邮箱发出来的一封测试邮件。说明邮箱通知确实已经配置正确并能够正常收发

Jenkins的通知邮件了。

2、项目配置

在项目的设置中找到“增加构建后的操作步骤”/"Add post-build Actions"，选择“E-mail Notifacation”通过E-mail通知。![](/assets/jenkins/jenkins_post_build_email_notification.png)如果配置没有问题，在构建出问题的时候都会有邮件通知到邮件通知接收者。

### 二、Email Extension Plugin插件配置邮件通知

1、全局配置

**Jenkins -&gt; Manage Jenkins -&gt; Configure System**![](/assets/jenkins/jenkins_global_ext_email_notification.png)

2、项目配置

