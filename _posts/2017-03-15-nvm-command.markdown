---
layout: post
title: Using nvm
date: 2017-03-15
comments: true
external-url:
categories: Ember.js
---

 nvm 安装和使用

`curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash`
<br>


>完成后nvm就被安装在了~/.nvm下了，接下来就需要配一下环境变量了，如果使用了zsh的话，就需要在~/.zshrc这个配置文件中配置，否则就找找看~/.bash_profile或者~/.profile。
打开`~/.zshrc`，在最后一行加上：

```
export NVM_DIR="$HOME/.nvm"
[ -s"$NVM_DIR/nvm.sh"] && ."$NVM_DIR/nvm.sh"# This loads nvm
```
>这一步的作用是每次新打开一个bash，nvm都会被自动添加到环境变量中了。
完成后输入source ~/.zshrc重新启动一下配置。



`nvm ls`

`nvm install stable`

`nvm install 7.7.3`

`nvm use 7`

`nvm alias default 7.7.3`

`npm install -g bower`

`npm install -g ember-cli`

`bower install <package>`

`coffee -c test.coffee`
