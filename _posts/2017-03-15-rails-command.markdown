---
layout: post
title: rails commline
date: 2017-03-15
comments: true
external-url:
categories: rails
---

rails常用的命令汇总：
1、rails new

`rails _4.2.17_ new myapp`

`rails new demo --skip-test-unit` or `rails new demo -T`

`rails new demo -d mysql -T`

`rails generate rspec:install` 初始化 Rspec

`rails new -h`

2、rails generate

`rails g controller user index` 生成 controller、路由、views、helper、及assets

`rails g model User name: string `生成 migration 文件及 model
 
`rails g mailer send_code code`  生成 mailer及view 文件

`rails g job send_mail`  生成 job，rails 4

`rails d model User`  rails destroy 命令理解为 rails generate 的反命令,`rails d` 是 rails destroy 的简写形式。

`rails generate -h`

3、 rails server

`rails s -p 4000 -e production`

4、rails console

`rails c`

[http://starzhou.com/blogs/rails_console_tips](http://starzhou.com/blogs/rails_console_tips)

5、`rails dbconsole` or  `rails db` 直接打开你配置数据库的终端

6、rails runner

` rails r "p Message.last"`

<hr>

7、rake

`rake -T`

`rake about`

`rake assets:precompile`

`rake assets:clean`

`rake db:migrate`

`rake db:migrate VERSION=1` 执行所有 version 为 1 之前的 migration;

`rake db:rollback`

`rake db:rollback STEP=3`

`rake db:seed` 根据 db/seeds.rb 文件初始化数据库数据;

`rake db:setup` 创建数据库，load schema 并使用 seed 数据初始化;

`rake routes`

### 参考：
1、[http://www.tuicool.com/articles/emaQJv3](http://www.tuicool.com/articles/emaQJv3)
2、[http://www.tuicool.com/articles/BZfmIvA](http://www.tuicool.com/articles/BZfmIvA)