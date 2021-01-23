---
layout: post 
title: Install rails 6
date: 2020-10-26
comments: true
external-url:
categories: Rails
---

Rails6与Rails5的不同在于引入webpack与yarn工具,因此需要安装相应的环境;

Rails6搭建的环境版本为 node v12.9.0，ruby v2.6.5，rails v6.0.3.4, nvm v0.36, yarn v1.22.5 

- rvm 安装 由于网络问题，采用本地安装，见rvm的使用
- rvm 安装 ruby 2.6.5
- 建立一个gemset 2.6.5@rails6
- 安装nvm 网络问题用git 方式

```
  
    git clone https://github.com/nvm-sh/nvm.git .nvm
    cd ~/.nvm
    git checkout v0.36.0
    . nvm.sh
```
添加内容到文件 ~/.profile

```
    export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
> [github:https://github.com/nvm-sh/nvm ](https://github.com/nvm-sh/nvm)

- 安装 node
```
    nvm install v12.9.0
```
- 安装yarn

```
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
    sudo apt update && sudo apt install yarn
```
- 安装rails6 

```
    gem install rails --version=6.0.3  --no-document
```
- 使用rails

```
    rails new hello_app # 自动运行webpack与yarn
    bundle update
    rails webpacker:install
    rails s -b 0.0.0.0 # 确保已进入项目的根目录,运行项目
```
---
> 如果bundle出现`TZInfo::DataSourceNotFound: tzinfo-data is not present`,编辑Gemfile
 把`gem 'tzinfo-data'`后面的, `platforms: [:mingw, :mswin, :x64_mingw, :jruby]`删除保留下面的
`gem 'tzinfo-data'`


> 参考：[blog](https://www.rubyc.cn/posts/33-Ubuntu16-04%E6%90%AD%E5%BB%BARails6%E7%9A%84%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83)