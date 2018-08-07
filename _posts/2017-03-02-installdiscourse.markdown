---
layout: post
title: Install Discourse on Ucloud
date: 2017-03-02
comments: true
external-url:
categories: Ember.js
---

> 说起对ember.js的兴趣，我是从discourse 开始的。看了很多开源系统，对ember.js+rails的discourse很有感觉:功能比较完善，灵活、可配置性非常好，部署方便，瀑布流的主题布局模式也很符合未来论坛的趋势，于是在 ucloud 上租用了云主机，成功安装了discourse 的论坛系统，期间遇到一些小困难，在中文论坛版主和很多热心朋友的的指点下都克服了，这里表示特别感谢！这篇记录最早发表于discourse 中文论坛，是整理给各位想使用discourse的朋友做些参考。

[作者博客链接: cloudhan.me](http://www.cloudhan.me)<br>
[技术博客: symphonyh](https://symphonyh.github.io/)

### 1. 环境介绍
云主机的选择了ucloud 没什么理由，算是国内比较领先的厂商之一吧，技术支持还行，晚上安装时碰到问题也有值班工程师解答；
新版本的docker的安装要求操作系统必须是64位的，我用的ubuntu14.04 64位操作系统。
安装云主机碰到的**一个问题**是安装完ubuntu系统后外网防火墙80端口的绑定，要使用外网IP打开主机的网站，需要绑定外网IP地址，绑定时开始没有绑定外网防火墙80端口，造成浏览器输入外网IP地址，是无法打开的。

### 2. 安装docker
网上有不少安装docker的教程和文章，大多都是几年前的文章，作者写的都很认真，不过已经完全不适用了，自己也走了弯路所以建议安装docker 按照安装手册里面的[官方文档](https://docs.docker.com/engine/installation/linux/ubuntu/)。ubuntu的不同版本（12.04/14.04/15.10）略有区别，手册里也说的比较清晰，针对14.04版本，没遇到什么问题，需要命令权限的命令前加`sudo`过程如下：

>     现在是`2016年2月份`，如果您看到这篇文章在1年以后，注意不要被我误导了，看看最新官方文档比较好。

（1）首先检查linux内核版本，ubuntu14.04 内核版本,内核版本要求`3.10`以上；

```bash
$ sudo uname -r
```
（2） 安装ca证书；[为什么安装ca？](http://baike.baidu.com/link?url=r8dly5JDJAeiV_-Tp3PgOQ8PeYZzH6yzNvUueMZOyqDLIrVm357zP5e8oG-Nt2FCFkGiHYIeAwoTPHdvnlJm4K)
```bash
$ apt-get update
$ sudo apt-get install apt-transport-https ca-certificates
```
（3）追加新的Key；注意是`apt-key`不是`apt-get`

```bash
$ sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
```
（3）添加deb包安装源；

使用管理员权限打开（没有的话新创建这个文件）`/etc/apt/sources.list.d/docker.list`，添加下面内容到文件里；不同的ubuntu版本添加源有所不同，注意参照[官方文档](https://docs.docker.com/engine/installation/linux/ubuntu/);
```bash
deb https://apt.dockerproject.org/repo ubuntu-trusty main

```
添加完安装源，保存文档，注意具有管理员权限才能保存；
（4）更新deb安装包索引文件，删除已经有的旧的docker（如果有），验证安装文件信息正确与否；
```bash
$ apt-get update
$ apt-get purge lxc-docker
$ apt-cache policy docker-engine
```
（5）安装镜像扩展文件；
```bash
$ apt-get update
$ sudo apt-get install linux-image-extra-$(uname -r)
```
（6）安装`apparmor`Linux系统安全应用程序 参考：[Apparmor](http://baike.baidu.com/link?url=N5VZhSjbjC_jX0V-Ce5WMjW4d8uETrkP1x7dqTDUywSN_BzMZhySe9U8LVoQ6JRoMtObWH-nNl85mWuZYIxDS_)
```bash
$ sudo apt-get install apparmor
```
（7）可以安装`docker`了!
```bash
$ sudo apt-get update
$ sudo apt-get install docker-engine
```
（8）确认安装成功？ 
```bash
$ sudo service docker start
$ sudo docker run hello-world
```

### 3. 安装discourse
安装完docker你会觉得安装discourse是很简单的参[安装文档](https://github.com/discourse/discourse/blob/master/docs/INSTALL-cloud.md)只需要几个步骤：
```bash
mkdir /var/discourse
git clone https://github.com/discourse/discourse_docker.git /var/discourse
cd /var/discourse
cp samples/standalone.yml containers/app.yml
```
>      说明：

       * 首先是创建一个目录`/var/discourse`；

       * 克隆discourse镜像到刚创建的目录；

       * 进入目录`/var/discourse`；

       * 复制配置文件到当前目录下的`containers/`

### 4. `app.yml`的配置
说到重点了，安装discourse过程中，比较容易出错的就是配置文件内容的修改；这里把
要修改的部分分别说明一下：
```bash
templates:
  - "templates/postgres.template.yml"
  - "templates/redis.template.yml"
  - "templates/sshd.template.yml"
  - "templates/web.template.yml"
  - "templates/web.china.template.yml"
```
配置文件的这个部分，需要添加`- "templates/web.china.template.yml"`;否则在`./launcher bootstrap app`初始化时会报错`RuntimeError: ...`，原因得问GWF。
```bash
  ## on initial signup example'user1@example.com,user2@example.com'
  DISCOURSE_DEVELOPER_EMAILS: 'henry@outlook.com'
```
这里是开发者邮箱的设置，用于接收discoures论坛的官方邮件，只针对开发运营这个论坛的开发者。

```bash
  ## TODO: The domain name this Discourse instance will respond to
  DISCOURSE_HOSTNAME: 'weifuwu.ren'
```
域名设置没设么可说的，没有的话，用绑定的外网IP地址访问discourse也可以，购买了域名可以按照指南到域名管理界面，进行设置；
```bash
  DISCOURSE_SMTP_ADDRESS:smtp.mxchina.com
  DISCOURSE_SMTP_PORT:25
  DISCOURSE_SMTP_USER_NAME: info@weifuwu.ren
  DISCOURSE_SMTP_PASSWORD: xxxxxxx
  DISCOURSE_SMTP_ENABLE_START_TLS: true
  DISCOURSE_SMTP_AUTHENTICATION: login
  DISCOURSE_SMTP_OPENSSL_VERIFY_MODE: none
```
重点是在邮箱设置，我申请的阿里云邮箱
- `DISCOURSE_SMTP_PASSWORD: xxxxxxx`设置的就是邮箱密码；
- `DISCOURSE_SMTP_PORT:`端口设置25，
- `DISCOURSE_SMTP_ADDRESS:`Host是`smtp.mxchina.com`,



  DISCOURSE_SMTP_USER_NAME:  这里的设置最最重要的，这个邮箱又叫notification email 被用于发送所有重要系统邮件的邮箱地址。指定的域名必须正确设置 SPF、DKIM 和反向 PTR 记录以发送邮件。一般和域名绑定在一起，比如info@weifuwu.com 或者 admin@weifuwu.com 都行，这样收到邮件的发帖人或回复人感觉比较正式，使用这个邮箱也是最频繁的。关于SPF、DKIM设置有篇文章可[参考](http://www.wendangdaquan.com/Wdshow.asp?id=98332e836f1aff00bed51e7c)
如果您使用的阿里云的企业邮箱，域名解析后可以不用设置 SPF、DKIM 了已经设置好了，注意阿里云这里设置` DISCOURSE_SMTP_ADDRESS:smtp.mxhichina.com`

### 5. 初始化
修改完app.yml配置文件，按照[安装文档](https://github.com/discourse/discourse/blob/master/docs/INSTALL-cloud.md)就可以进行初始化了，（耐心等待一段时间，我的云主机大概5分钟吧）：
```bash
./launcher bootstrap app
```
启动discourse服务，就OK了！
```bash
./launcher start app
```
如果再次修改了配置文件也可以用：
```bash
./launcher rebuild app
```
试过了，这两个命令不会删除数据，放心用就行；docker的数据和容器是分离的，这是docker的优点吧。

现在应该可以登陆网站了，使用设置的域名或外网Ip地址；如果发现没有收到管理员激活邮件，也可以手动建立一个管理员账户：
```bash
./launcher enter app
rake admin:create
exit
```
按照提示输入邮箱和密码，exit退出容器。


>最后特别提示下：管理员邮箱，也就是用rake admin:create 创建的邮箱一般用于设置论坛；DISCOURSE_SMTP_USER_NAME 邮箱用于论坛接收、发送信息给（创建主题、发帖、回复等等）使用者；DISCOURSE_DEVELOPER_EMAILS开发者邮箱用于论坛给开发运营论坛的人的官方邮件；三个邮箱作用不同，可以设置三个不同邮箱，也可以相同。

### 参考

>1、[Get Docker for Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/)；
