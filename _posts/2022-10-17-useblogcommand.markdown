---
layout: post
title: Blog 推送的常用指令
date: 2022-10-17
comments: true
external-url:
categories: Ruby 
---

rvm gemset切换:
~~~
rvm use 2.7.0@jekyll 
rvm use 2.7.0@rails
~~~
---

blog 推送的操作:

~~~
git checkout -b gh-pages
git add .
git commit -m "sailing race"
git push origin gh-pages

~~~
---

symphonyh.io推送的操作:

~~~
git add .
git commit -m "XXX"
git push origin master
~~~
---

清理ubuntu:

~~~
sudo apt-get autoclean                清理旧版本的软件缓存
sudo apt-get clean                    清理所有软件缓存
sudo apt-get autoremove             删除系统不再使用的孤立软件
~~~

---

设置git命令
~~~
  git config --global user.name "hxygsh@outlook.com"
  git config --global user.name "symphonyh"
  git config --global color.ui auto
  git config --global credential.helper store 提交不再每次输入密码
~~~


查看git设置:
~~~
git config --list
~~~

生成公匙:
~~~
ssh-keygen -t rsa -C "hxygsh@outlook.com" 
~~~
*生成公匙，就是 id_rsa.pub 这个文件，里面内容要写入GitHub的 SSH*


验证公匙:
~~~
ssh -T git@github.com
~~~

获取远程库:

~~~
git clone https://github.com/symphonyh/blog.git
git clone  https://github.com/symphonyh/symphonyh.github.io
~~~

---

token 验证：

~~~
git remote set-url origin  https:// token @github.com/symphonyh/symphonyh.github.io.git

git remote set-url origin  https:// token @github.com/symphonyh/blog.git
~~~
*需要将token替换为实际值*