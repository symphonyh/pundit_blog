---
layout: post
title: Blog 推送的常用指令
date: 2020-10-05
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