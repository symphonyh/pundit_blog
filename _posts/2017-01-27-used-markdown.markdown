---
layout: post
title:  Markdown 语法整理
date: 2017-01-27
comments: true
external-url:
categories: Template-language
---

Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。

1.<a>标题</a><br>
   在Markdown当中设置标题，有两种方式：
   - 通过在文字下方添加“=”和“-”，他们分别表示一级标题二级标题。
   - 在文字开头加上 “#”，通过“#”数量表示几级标题。
   >     共有1~6级标题，1级标题字体最大

2.<a>块注释（blockquote）</a><br>
   通过在文字开头添加“>”表示块注释。
>      当>和文字之间添加五个blank时，块注释的文字会有变化。


3.<a>斜体</a><br>
将需要设置为斜体的文字两端使用1个“*”或者“_”夹起来

4.<a>粗体</a><br>
将需要设置为斜体的文字两端使用2个“*”或者“_”夹起来

5.<a>无序列表</a><br>
在文字开头添加(\*, +, or -)实现无序列表。但是要注意在(\*, +, and -)和文字之间需要添加空格。
>       建议：一个文档中只是用一种无序列表的表示方式

6.<a>有序列表</a><br>
使用数字后面跟上句号。**记得还要有空格**

7.<a>链接 (Links)</a><br>
   Markdown中有两种方式，实现链接，分别为内联方式和引用方式。
   - 内联方式：`This is an [example link](http://example.com/).`
   - 引用方式：

```
   I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

   [1]: http://google.com/        "Google" 
   [2]: http://search.yahoo.com/  "Yahoo Search" 
   [3]: http://search.msn.com/    "MSN Search"
```

8.<a>图片(Images)</a><br>
   图片的处理方式和链接的处理方式，非常的类似。
   - 内联方式：`![alt text](/path/to/img.jpg "Title")`
   - 引用方式：

```
    ![alt text][id]

    [id]: /path/to/img.jpg "Title"

    <div align=center><img width = '150' height ='150' src ="https://tse2-mm.cn.bing.net/th?id=OIP.rF3VYN1CRvtyWBPU0I7kyQDMEy&p=0&pid=1.1"/></div>
```

9.<a>代码块</a><br>
    实现方式有两种：
   - 简单文字出现一个代码框。使用`<blockquote>`。
>      不是单引号而是左上角的ESC下面~中的"`"）
   - 大片文字需要实现代码框。使用Tab和四个空格。

10.<a>脚注(footnote)</a><br>

```
hello[^hello]
...

[^hello]: hi

```

11.<a>下划线</a><br>
在**空白行**下方添加三条“-”横线。
>      前面讲过在文字下方添加“-”，实现的2级标题

12.<a>注释</a>
HTML 以 `<!-- , --> `的闭包定义注释（支持跨行），不在正文中显示。Markdown 沿用 HTML Comment 注释格式：

`<!-- This text will not appear in the browser window. --> `

13.<a>关于字体</a> 

  字体颜色：

~~~
浅红色文字：<font color="#dd0000">浅红色文字：</font><br /> 

深红色文字：<font color="#660000">深红色文字</font><br /> 

浅绿色文字：<font color="#00dd00">浅绿色文字</font><br /> 

深绿色文字：<font color="#006600">深绿色文字</font><br /> 

浅蓝色文字：<font color="#0000dd">浅蓝色文字</font><br /> 

深蓝色文字：<font color="#000066">深蓝色文字</font><br /> 

浅黄色文字：<font color="#dddd00">浅黄色文字</font><br /> 

深黄色文字：<font color="#666600">深黄色文字</font><br /> 

浅青色文字：<font color="#00dddd">浅青色文字</font><br /> 

深青色文字：<font color="#006666">深青色文字</font><br /> 

浅紫色文字：<font color="#dd00dd">浅紫色文字</font><br /> 

深紫色文字：<font color="#660066">深紫色文字</font><br /> 

~~~
深紫色文字：<font color="#660066">深紫色文字</font><br /> 
深红色文字：<font color="#660000">深红色文字</font><br /> 

字体大小：

~~~
size为1：<font size="1">size为1</font><br /> 
size为2：<font size="2">size为2</font><br /> 
size为3：<font size="3">size为3</font><br /> 
~~~
size为1：<font size="1">size为1</font><br />
size为2：<font size="2">size为2</font><br /> 
size为3：<font size="3">size为3</font><br /> 

字体背景颜色：

~~~
<table><tr><td bgcolor=#FF00FF>背景色的设置是按照十六进制颜色值：#7FFFD4</td></tr></table>
<table><tr><td bgcolor=#FF83FA>背景色的设置是按照十六进制颜色值：#FF83FA</td></tr></table>
<table><tr><td bgcolor=#D1EEEE>背景色的设置是按照十六进制颜色值：#D1EEEE</td></tr></table>
<table><tr><td bgcolor=#C0FF3E>背景色的设置是按照十六进制颜色值：#C0FF3E</td></tr></table>
~~~

文字居中：

~~~
<center>Hello</center>
~~~
<center>Hello</center>
文字左对齐：

~~~
<p align="left">Hello</p>
~~~
<p align="left">Hello</p>

使用字体：

~~~
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
~~~


14.<a>关于音频、视频</a> 
 
插入音频：

~~~
<audio id="audio" controls="" preload="none">
      <source id="mp3" src="http://oht4nlntk.bkt.clouddn.com/Music_iP%E8%B5%B5%E9%9C%B2%20-%20%E7%A6%BB%E6%AD%8C%20%28Live%29.mp3">
      </audio>
~~~


---

<audio id="audio" controls="" preload="none">
      <source id="mp3" src="http://oht4nlntk.bkt.clouddn.com/Music_iP%E8%B5%B5%E9%9C%B2%20-%20%E7%A6%BB%E6%AD%8C%20%28Live%29.mp3">
      </audio>


<br>
插入视频：

第一种方式：
~~~
<iframe 
    width="800" 
    height="450" 
    src="https://v.miaopai.com/iframe?scid=SvyHaHOczsp7B6ftW86oqMMz62-h5ai6~Fwp8A__"
    frameborder="0" 
    allowfullscreen>
</iframe>
~~~
<iframe 
    width="800" 
    height="450" 
    src="https://v.miaopai.com/iframe?scid=SvyHaHOczsp7B6ftW86oqMMz62-h5ai6~Fwp8A__"
    frameborder="0" 
    allowfullscreen>
</iframe>

---
第二种方式，自动播放：
~~~
<iframe width="560" height="315" src="http://tv.sohu.com/upload/static/share/share_play.html#90268916_9365222_0_9001_0" frameborder="0" allowfullscreen></iframe>
~~~

第三种方式：
~~~
<video id="video" controls="" preload="none" poster="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.jpg">
      <source id="mp4" src="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.mp4" type="video/mp4">
      </video>
~~~


<video id="video" controls="" preload="none" poster="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.jpg">
      <source id="mp4" src="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.mp4" type="video/mp4">
      </video>


15.<a>跳转链接</a>

~~~
<a href="http://askunix.top/" target="_blank">跳到自己博客列表</a>

跳到自己博客列表：<a href="http://askunix.top/" target="_blank">http://askunix.top/</a>
~~~

<br>
<hr>
<br>

### **范例**

>重点可以看下图片引用和表格对齐方式的用法。

```
# Fat Free CRM [![TravisCI][travis-img-url]][travis-ci-url]  [![Code Climate](https://codeclimate.com/github/fatfreecrm/fat_free_crm.png)](https://codeclimate.com/github/fatfreecrm/fat_free_crm)

[travis-img-url]: https://secure.travis-ci.org/fatfreecrm/fat_free_crm.png?branch=master
[travis-ci-url]: http://travis-ci.org/fatfreecrm/fat_free_crm

### An open source, Ruby on Rails [customer relationship management][crm-wiki] platform (CRM).

[crm-wiki]: http://en.wikipedia.org/wiki/Customer_relationship_management


<table>
  <tr>
    <td align="center">
      <a href="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/contact_create.png" target="_blank" title="Create Contacts">
        <img src="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/contact_create_t.png" alt="Create Contacts">
      </a>
      <br />
      <em>Contacts</em>
    </td>
    <td align="center">
      <a href="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/contact_opportunity.png" target="_blank" title="Manage Opportunities">
        <img src="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/contact_opportunity_t.png" alt="Manage Opportunities">
      </a>
      <br />
      <em>Opportunities</em>
    </td>
    <td align="center">
      <a href="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/account_edit.png" target="_blank" title="Edit Accounts">
        <img src="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/account_edit_t.png" alt="Edit Accounts">
      </a>
      <br />
      <em>Accounts</em>
    </td>
    <td align="center">
      <a href="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/task_create.png" target="_blank" title="Create Tasks">
        <img src="https://github.com/fatfreecrm/fatfreecrm.github.com/raw/master/images/task_create_t.png" alt="Create Tasks">
      </a>
      <br />
      <em>Tasks</em>
    </td>
  </tr>
</table>

Pull requests and bug reports are always welcome!

Visit our website at http://www.fatfreecrm.com/

## Rails 4 support

The master branch is now on Rails 4.2. However, there is a [Rails 3.2 branch](https://github.com/fatfreecrm/fat_free_crm/tree/rails3) available if you still need to use it. Please note that subsequent gem releases will focus on Rails 4 (v0.14.0+ as yet unreleased).



## System Requirements

* Ruby 2 (2.2 recommended)
  * Ruby 1.9.3 is no longer compatible (final gem release tag v0.13.6)
  * Ruby v1.8.7 was supported until v0.11.4 (see https://github.com/fatfreecrm/fat_free_crm/tree/ruby1.8)
* MySQL v4.1.1 or later (v5+ is recommended), SQLite v3.4 or later, or Postgres 8.4.8 or later.
* ImageMagick (optional, only needed if you would like to use avatars)

(Ruby on Rails and other gem dependencies will be installed automatically by Bundler.)


## Installation

Please view one of the following installation guides:

### [Setup Linux or Mac OS](http://guides.fatfreecrm.com/Setup-Linux-or-Mac-OS.html)

Installing Fat Free CRM on Linux or Mac OS X



## Upgrading from previous versions of Fat Free CRM

Please read the [Release Notes](https://github.com/fatfreecrm/fat_free_crm/blob/master/CHANGELOG) document for more detailed information on upgrading from previous versions.


## Resources

|||
|-----------------------------------:|:--------------------------|
|                 **Home Page**: | http://www.fatfreecrm.com |
|                    **Guides**: | http://guides.fatfreecrm.com |
|               **Online Demo**: | http://demo.fatfreecrm.com |
|       **Github Project Page**: | http://github.com/fatfreecrm/fat_free_crm |
| **Feature Requests and Bugs**: | http://support.fatfreecrm.com/ |
|                  **RDoc API**: | http://api.fatfreecrm.com |
|                  **Ruby gem**: | https://rubygems.org/gems/fat_free_crm |
|    **Twitter Commit Updates**: | http://twitter.com/fatfreecrm |
|       **User's Google Group**: | http://groups.google.com/group/fat-free-crm-users |
|  **Developer's Google Group**: | http://groups.google.com/group/fat-free-crm-dev |
|               **IRC Channel**: | [#fatfreecrm](http://webchat.freenode.net/) on irc.freenode.net |





## Main contributors

* [Michael Dvorkin (@michaeldv)](https://github.com/michaeldv) - Founding creator
* [Steve Kenworthy (@steveyken)](https://github.com/steveyken) - Maintainer
* [Nathan Broadbent (@ndbroadbent)](https://github.com/ndbroadbent)


```
![页面效果展示](/image/markdown1.jpg)
<br>
![页面效果展示](/image/markdown2.jpg)
<hr style="margin: 45px">
### <a>参考</a><br>

>1、[Markdown 语法说明](http://wowubuntu.com/markdown/)；
 2、[本文转自互联网360doc](http://www.360doc.com/content/15/0216/11/8790037_448944940.shtml).

