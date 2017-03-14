---
layout: post
title: Git Commline
date: 2017-03-12
comments: true
external-url:
categories: ruby
---
git 经常用到的一些命令汇总.
<hr>

`git init`:                                   将目标目录变为git可管理的仓库

`git add file.txt` :                       添加文件到暂存区

`git add .` or `git add -A` :   添加所有修改到暂存区

`git add -p` : 交互式提交

`git commit -m "first commit"`:          将文件提交到仓库，双引号中为注释

`git status`:                              查看仓库状态，看是否还有文件未提交

 `git blame [filename]`: 如果你要查看文件的每个部分是谁修改的, 那么 git blame 就是不二选择. 只要运行'git blame [filename]', 你就会得到整个文件的每一行的详细修改信息:包括SHA串,日期和作者.

<hr>

`git diff file.txt `:                         查看file.txt文件里更改的内容

`git diff`:       查看没有add的内容修改

`git diff HEAD`:   工作目录和上次提交的修改

`git diff --staged`:  查看已经add没有commit的修改，相对于工作区 
<hr>

`git log`:                                   查看历史纪录

`git reflog`:                              获取之前的提交列表
<hr>

`git reset --hard HEAD^`:     退回/找回上一个版本

`git reset --hard HEAD^^`:   退回/找回上上个版本

`git reset --hard HEAD~3`:  会将最新的3次提交全部重置，就像没有提交过一样

`git reset --hard b7057a9`:           回到b7057a9版本

```bash
git reset --hard

git clean -df
```
>使用命令组合会使工作目录和缓存区回到最近一次commit时候一摸一样的状态, `git status`会告诉你这是一个干净的工作目录, 又是一个新的开始了.(删除所有工作目录下面的修改, 包括新添加的文件. 假设你已经提交了一些快照了, 而且做了一些新的开发)
<hr>

`git checkout`:                    汇总显示工作区、暂存区与HEAD的差异

`git checkout -- file.txt`: <br />           撤销file.txt文件在工作区所做的修改，用暂存区中文件来覆盖工作区中的文件;相当于取消自上次执行`git add` 以来（如果执行过）的本地修改

`git checkout . `: <br />
会取消所有本地的 修改（相对于暂存区）,相当于用暂存区的所有文件直接覆盖本地文件，不给用户任何确认的机会！

<hr>

`cat file.txt `:                               查看file.txt文件里的内容

`git rm file.txt`:                                 删除file.txt文件

`git mv b.txt c.txt `:             修改文件名
<hr>

分支管理：
git merge --no-ff -m "merge with no-ff" dev    合并dev分支 -no-ff表示禁用fast forward  

创建与合并分支：
git checkout -b XXX           创建并切换分支XXX
git branch                            查看当前分支
git branch XXX                   创建分支XXX
git checkout XXX               切换分支至XXX
git merge XXX                     合并XXX分支到当前分支
git branch -d XXX             删除XXX分支
<hr>

- 本地到远程：

`git remote add origin https://github.com/try-git/try_git.git`: <br /> 
推送本地仓库的内容至GitHub仓库

`git push -u origin master`:   <br />
    把本地仓库分支master内容推送到远程库（-u是因为远程库是空）

`git push origin master`:           将本地master分支的最新修改推送到GitHub上


- 远程到本地：

`git clone git@github.com:symphonyh/forum.rb.git`: <br />
 将github上的远程库克隆到本地库并且具有读写权限

`git pull origin master`:    把github上的更改（其他开发者）拉回到本地master

**github上的版本强行覆盖本地文件:**

```bash
git fetch --all  
git reset --hard origin/master
```
<hr>
