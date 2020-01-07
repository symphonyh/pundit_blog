---
layout: post
title: 配置安装manjaro的过程记录
date: 2020-01-04
comments: true
external-url:
categories: Javascript
---

manjaro 安装记录

>pacman 命令行参考 [pacman 命令汇总贴 ](https://blog.csdn.net/nangy2514/article/details/93194184#4__49)

---

### 1、选择国内源

`sudo pacman-mirrors -i -c China -m rank ` 

修改pacman.conf

`sudo mousepad /etc/pacman.conf `

更新系统 

`sudo pacman -Syu`

安装 archlinuxcn-keyring 包导入GPG key

`sudo pacman -S archlinuxcn-keyring `

### 2、安装输入法：

```
sudo pacman -S fcitx-im
sudo pacman -S fcitx-configtool
sudo pacman -S fcitx-sogoupinyin
```

`sudo mousepad  ~/.xprofile`复制下面内容到文件

```
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```


### 3、安装中文字体，调整终端显示

```
sudo pacman -S wqy-microhei
sudo pacman -S wqy-bitmapfont
```

安装monaco终端字体

```
./install-font-archlinux.sh https://github.com/todylu/monaco.ttf/blob/master/monaco.ttf?raw=true
```

### 4、配置git

```
git -v
gem -v
```
配置github的密匙，在github网页SSH添加密匙 .pub

`ssh-keygen -t rsa -C "hxygsh@outlook.com"`

### 5、安装ruby

```
sudo pacman -S ruby ruby-docs rubygems
ruby -v
```

### 6、gem 更换源

```
gem sources -l
gem sources --remove https://rubygems.org/
gem sources -a https://gems.ruby-china.com
gem sources -l
```


### 7、克隆博客

`git clone git@github.com:symphonyh/symphonyh.github.io.git`


`git clone git@github.com:symphonyh/symphonyh.github.io.git`


### 8、安装jekyll

`gem install jekyll 4.0.0`

配置环境变量（重要）

```
查看路径
which jekyll
gem environment
echo $PATH
```
`export PATH="/home/cloudha/.gem/ruby/2.6.0/bin:$PATH" `  路径放到`.profile`文件中

>[百度了半天还是参考的这个帖子弄明白了https://blog.csdn.net/qq_34879948/article/details/91129769](https://blog.csdn.net/qq_34879948/article/details/91129769)

`jekyll -v`

`gem list jekyll`

blog 运行jekyll 需要执行`bundle install`

`gem install bundle`


---

### 9、共享文件夹一致没解决，重装增强模块也没用，待解决

```
sudo su
mkdir sarah
sudo mkdir sarah
ls
sudo mount -t vboxsf sarahtree /mnt/sarah

pacman -Ss linux-headers 查找可用内核
sudo pacman -S linux54 linux54-headers

sudo ./VBoxLinuxAdditions.run
```