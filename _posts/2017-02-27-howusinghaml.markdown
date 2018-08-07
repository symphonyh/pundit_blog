---
layout: post
title: How using haml
date: 2017-01-17
comments: true
external-url:
categories: Template-language
---


haml 是一种简洁优美的模板语言，主要智能用来替代基于`ruby`框架的模版系统，例如：替换`Ruby on Rails`的`erb`模版，可以大大缩减模板代码，减少冗余，提高可读性。并且Haml是一种完备的模板语言，没有牺牲当前模板语言的任何特性。Haml由`Hampton Catlin`发明并且开发了`Ruby on Rails`上的实现。

### 一、概述

1.常见语法规则

||||
|----:|:----|:---|
| 序号 | haml | html |
|----|------|------|
| 1. | !!!5 | <!DOCTYPE html> |
| 2. | %tag | 代表HTML标签 |
| 3. | %tag#id | 代表id属性 |
| 4. | %tag.class | 代表class属性 |
| 5. | %tag(attr="xxx") | 代表某一个特定属性 |
| 6. | %tag xxx | 代表插入标签的内容 |
| 7. | %E %N | 代表N是E的子元素。N如果写在第二行，需要缩进**‘二格’** |
| 8. | \| | haml标签，多行连接符 |
| 9. | -# | haml注释 |
| 10. | / | haml标签，前面加单行或多行注释，后面加关闭标签 |

>      `tag`,`E`可以替换为html标签 `<p>,<a>,<ul>,<li>,<stong>,<title>...`

　
2.haml 范例

```haml
!!! 5
　　%html{lang: 'en'}
　　　　%head
　　　　　　%title Haml Demo
　　　　%body
　　　　　　%h1 Hello World
　　　　　　%a(href="http://wikipedia.org" title="Wikipedia") 维基百科
```
to HTML：

```html
　　<!DOCTYPE html>
　　<html lang='en'>
　　　　<head>
　　　　　　<title>Haml Demo</title>
　　　　</head>
　　　　<body>
　　　　　　<h1>Hello World</h1>
　　　　　　<a href='http://wikipedia.org' title='Wikipedia'>维基百科</a>
　　　　</body>
　　</html>
　　
```
### 二、语法 (on rails)
1.**%** 百分号符号是一行的开始，紧接着一个元素的名字，它会创建一个这样的形式：**<element></element>**,  默认的元素是**div**;

`%strong test `   to HTML：`<strong>test</strong>`

 `strong= item.title`    to ERB：`<strong><%= item.title %></strong>`
<br>
  
2.**#** 代替 **id**

`#id= item.title`         to ERB:    `<div id="id"><%= item.title %></div>`  
<br>

3.**"."** 代替 **class**

`%strong.code#message Hello, World!`  to ERB: 

 `<strong><class=code id="message">Hello, World!<strong>`

 >      3,4,5标题中"" 是为了方便读者看清，语句实际使用中并不需要;

<br>
4.**"="** 代替 **<%= %>** 相当于插入ruby代码,并输出结果;

`.my-class= item.title`     to ERB: `<div class="my-class"><%= item.title %></div>`
<br>

`%p= Time.now` to HTML:`<p>Sat Aug 06 15:06:09 +0100 2011</p>`
<br>

5.**"-"** 代替 **<%  %>**相当于执行ruby代码,但不输出结果;

```
  - if @opportunities.any?
    = render @opportunities
  - else
    = render "shared/empty"
```
to ERB:

```
<%if @opportunities.any? %>
  <%= render @opportunities %>
<%else%>
  <%= render "shared/empty" %>
<%end%>
```
<br>
6.**#{}** 表示插入ruby代码,并计算结果;

`%script(type="text/javascript" src="javascripts/script_#{2 + 7}")` to HTML:

`<script type="text/javascript" src="javascripts/script_9"></script>`


>     常见的a标签和span标签:

```
%a(title=@title){:href => @link.href} Stuff

%span(class="widget_#{@widget.number}")
```
<br>
7.**{}** 添加的ruby hash 属性或 html 复杂代码,hash属性和值之间用 **{:属性1=> 值1,:属性2=> 值2 }**表示;

`%strong{:class=>"code",:id=>"message"} Hello, World!` to ERB: 

`<strong><class="code" id="message">Hello, World!<strong>` 

<br>
8.**img**标签hash

`%img{ :src => "/path/to/image", :alt => "Description of image" }` or

`%img ( src="/path/to/image", alt="Description of image")`

to HTML：

`<img src="/path/to/image" alt="Description of image">`

<br>
9.HTML5 DOCTYPE


`!!!5`  to HTML: `<!DOCTYPE html>`


`%meta{ :charset => "utf-8" }` to HTML:`<meta charset="utf-8"> `

<br>

`%link{ :rel => "stylesheet", :href => "/css/master.css" }` to HTML:

`<link rel="stylesheet" href="/css/master.css">`

<br>

`%script{ :src => "/js/site.js" }` to HTML:

`<script src="/js/site.js"></script>`
<br>
10.注释语句

- **/** 表示注释,分为行注释和块注释;

```
/ A forward slash at the start of a line wraps that line in a comment  
%blockquote  
  %p Roads? Where we're going we don't need roads
  
/  
  A forward slash at the start of a nested block wraps the whole block in a comment  
  %blockquote  
    %p Roads? Where we're going we don't need roads
```

```html
<!-- Only this line will be wrapped in a comment --> 
<blockquote> 
  <p>Roads? Where we're going we don't need roads</p> 
</blockquote> 

<!-- 
  Now the whole block will be commented out 
  <blockquote> 
    <p>Roads? Where we're going we don't need roads</p> 
  </blockquote> 
-->
```
<br>
- **/[ ]**表示条件注释;

`/[if IE] %link { :rel => "stylesheet", :href => "/css/ie.css" }` to HTML:

`<!--[if IE]> <link href="/css/ie.css" rel="stylesheet"> <![endif]-->`
<br>
- **-#**表示haml自带注释;

```
%p The line below won't appear in the HTML 
-# The rest of this line is a comment 
%p The line above won't appear in the HTML, nor will the lines underneath 
-# 
  None of this nested text will appear 
  in our rendered output either
```


```html
<p>The line below won't appear in the HTML</p> 
<p>The line above won't appear in the HTML, nor will the lines underneath</p>
```

### 三、安装 Installing Haml

`gem install haml` or

Gemfile中添加: 
```
  gem 'haml'
  gem "haml-rails"
```

安装后可以运行halm使用命令行：

`haml input.html.haml output.html`



<hr style="margin: 60px">
### 参考

>1、[HTML代码简写法：Emmet和Haml](http://www.ruanyifeng.com/blog/2013/06/emmet_and_haml.html)；
 2、[An Introduction to Haml](https://www.sitepoint.com/an-introduction-to-haml/)


