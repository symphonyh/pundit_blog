---
layout: post
title:  Markdown 语法整理
date: 2017-01-27
comments: true
external-url:
categories: Template-language
---

Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式,更加便于书写和阅读。

### &sect;&nbsp;标题

   在`Markdown`当中设置标题，有两种方式：

   - 通过在文字下方添加`=`和`-`，他们分别表示一级标题二级标题。

   - 在文字开头加上 `#`，通过`#`数量表示几级标题。

   >     共有1~6级标题，1级标题字体最大。

### &sect;&nbsp;块注释（blockquote）

   通过在文字开头添加`>`表示块注释。

>     当`>`和文字之间添加五个空格时，块注释的文字会有变化。



### &sect;&nbsp;无序列表

在文字开头添加(\*, +, or -)实现无序列表。但是要注意在(\*, +, and -)和文字之间需要添加空格。

>     建议：一个文档中只是用一种无序列表的表示方式

## &sect;&nbsp;有序列表

使用数字后面跟上句号。**记得还要有空格**

### &sect;&nbsp;链接 (Links)

   Markdown中有两种方式，实现链接，分别为内联方式和引用方式。

   - 内联方式：`This is an [example link](http://example.com/).`

   - 引用方式：


   I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

   [1]: http://google.com/        "Google" 
   [2]: http://search.yahoo.com/  "Yahoo Search" 
   [3]: http://search.msn.com/    "MSN Search"

~~~
   I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

   [1]: http://google.com/        "Google" 
   [2]: http://search.yahoo.com/  "Yahoo Search" 
   [3]: http://search.msn.com/    "MSN Search"
~~~

   - 链接跳转:

~~~
<a href="https://cloudhan.me"  target="_blank">跳到自己博客列表</a>

跳到自己博客列表：<a href="https://cloudhan.me" target="_blank">cloudhan</a>
~~~


### &sect;&nbsp; 图片(Images)

图片的处理方式和链接的处理方式，非常的类似。

   - 内联方式：`![alt text](/path/to/img.jpg "Title")`

   - 引用方式：

```
![alt text][id]

[id]: /path/to/img.jpg "Title"

```
- html的处理方式：

~~~
<img src="/assets/bella.jpg" alt="Het meisje met de parel" width="400px" height="200px" style="margin:0"> 

<div align=center><img width = '150' height ='150' src ="https://tse2-mm.cn.bing.net/th?id=OIP.rF3VYN1CRvtyWBPU0I7kyQDMEy&p=0&pid=1.1"/></div>
~~~

### &sect;&nbsp;代码块（code/pre）

实现方式有两种：
- 简单文字出现一个代码框(code)。使用`<blockquote>`。
>      不是单引号而是左上角的ESC下面~中的"`"）

- 大片文字需要实现代码框(pre)，使用Tab和四个空格，或者`~~~`包围代码。


### &sect;&nbsp;脚注(footnote)

~~~
hello[^1]
...

[^1]: 这是一个注解。

~~~

### &sect;&nbsp;下划线

在**空白行**下方添加`---`横线。

>      前面讲过在文字下方添加“-”，实现的2级标题


### &sect;&nbsp;注释 

HTML 以 `<!-- , --> `的闭包定义注释（支持跨行），不在正文中显示。Markdown 沿用 HTML Comment 注释格式：

`<!-- This text will not appear in the browser window. --> `


### &sect;&nbsp;关于字体 

*斜体*:将需要设置为斜体的文字两端使用1个`*`或者`_`夹起来

**粗体**:将需要设置为斜体的文字两端使用2个`*`或者`_`夹起来

字体颜色：

~~~
浅红色文字：<font color="#dd0000">浅红色文字：</font><br /> 

深红色文字：<font color="#bd4147">深红色文字</font><br /> 

~~~

文字颜色：<font color="#bd4147">当前文本文字</font> 

字体大小：
~~~
size为1：<font size="1">size为1</font><br /> 
size为2：<font size="2">size为2</font><br /> 
size为3：<font size="3">size为3</font><br /> 
~~~
size为1：<font size="1">size为1</font><br />
size为2：<font size="2">size为2</font><br /> 
size为3：<font size="3">size为3</font><br /> 

>字体大小为1-7,7号最大，3号为浏览器默认大小。

字体背景颜色：

~~~
<table><tr><td bgcolor="#FF00FF">背景色的设置是按照十六进制颜色值：#7FFFD4</td></tr></table>
<table><tr><td bgcolor="#FF83FA">背景色的设置是按照十六进制颜色值：#FF83FA</td></tr></table>
<table><tr><td bgcolor="#D1EEEE">背景色的设置是按照十六进制颜色值：#D1EEEE</td></tr></table>
<table><tr><td bgcolor="#C0FF3E">背景色的设置是按照十六进制颜色值：#C0FF3E</td></tr></table>
~~~

<table>
  <tr>
    <td bgcolor="#C0FF3E">
背景色的设置是按照十六进制颜色值：#C0FF3E
    </td>
  </tr>
</table>

>测试了下，除了表格可以用，其他标签不起作用，不建议使用这个属性。

文字居中：

~~~
<center>Hello</center>
~~~

文字左对齐：

~~~
<p align="left">Hello</p>
~~~

使用常用字体：

~~~
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
~~~

---

### &sect;&nbsp;插入音频
 

~~~
<audio id="audio" controls="" preload="none">
  <source id="mp3" src="http://music.163.com/song/media/outer/url?id=562598065.mp3">
</audio>
~~~


---

<audio id="audio" controls="" preload="none">
  <source id="mp3" src="http://music.163.com/song/media/outer/url?id=562598065.mp3">
</audio>


### &sect;&nbsp;插入视频

- 第一种方式：

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
- 第二种方式，自动播放：

~~~
<iframe width="560" height="315" src="http://tv.sohu.com/upload/static/share/share_play.html#90268916_9365222_0_9001_0" frameborder="0" allowfullscreen></iframe>
~~~

---
- 第三种方式：

~~~
<video id="video" controls="" preload="none" poster="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.jpg">
      <source id="mp4" src="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.mp4" type="video/mp4">
      </video>
~~~


<video id="video" controls="" preload="none" poster="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.jpg">
      <source id="mp4" src="http://om2bks7xs.bkt.clouddn.com/2017-08-26-Markdown-Advance-Video.mp4" type="video/mp4">
      </video>

---
<br>

### 范例

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

