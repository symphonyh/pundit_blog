---
layout: post
title: Using markdown 
date: 2017-01-27
comments: true
external-url:
categories: template-language
---

### used markdown 

1.<a>标题</a>
   在Markdown当中设置标题，有两种方式：
   - 通过在文字下方添加“=”和“-”，他们分别表示一级标题二级标题。
   - 在文字开头加上 “#”，通过“#”数量表示几级标题。
   >     共有1~6级标题，1级标题字体最大

2.<a>块注释（blockquote）</a>
   通过在文字开头添加“>”表示块注释。
>      当>和文字之间添加五个blank时，块注释的文字会有变化。


3.<a>斜体</a>
将需要设置为斜体的文字两端使用1个“*”或者“_”夹起来

4.<a>粗体</a>
将需要设置为斜体的文字两端使用2个“*”或者“_”夹起来

5.<a>无序列表</a>
在文字开头添加(\*, +, or -)实现无序列表。但是要注意在(\*, +, and -)和文字之间需要添加空格。
>       建议：一个文档中只是用一种无序列表的表示方式

6.<a>有序列表</a>
使用数字后面跟上句号。**记得还要有空格**

7.<a>链接 (Links)</a>
   Markdown中有两种方式，实现链接，分别为内联方式和引用方式。
   - 内联方式：`This is an [example link](http://example.com/).`
   - 引用方式：

```
   I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

   [1]: http://google.com/        "Google" 
   [2]: http://search.yahoo.com/  "Yahoo Search" 
   [3]: http://search.msn.com/    "MSN Search"
```

8.<a>图片(Images)</a>
   图片的处理方式和链接的处理方式，非常的类似。
   - 内联方式：`![alt text](/path/to/img.jpg "Title")`
   - 引用方式：

```
    ![alt text][id]

    [id]: /path/to/img.jpg "Title"
```

9.<a>代码块</a>
    实现方式有两种：
   - 简单文字出现一个代码框。使用`<blockquote>`。
>      不是单引号而是左上角的ESC下面~中的"`"）
   - 大片文字需要实现代码框。使用Tab和四个空格。

10.<a>脚注(footnote)</a>

```
hello[^hello]
...

[^hello]: hi

```

11.<a>下划线</a>
在**空白行**下方添加三条“-”横线。
>      前面讲过在文字下方添加“-”，实现的2级标题

12.<a>注释</a>
HTML 以 `<!-- , --> `的闭包定义注释（支持跨行），不在正文中显示。Markdown 沿用 HTML Comment 注释格式：

`<!-- This text will not appear in the browser window. --> `

<hr style="margin: 45px">
### <a>参考</a>

>1、[Markdown 语法说明](http://wowubuntu.com/markdown/)；
 2、[本文转自互联网](http://www.360doc.com/content/15/0216/11/8790037_448944940.shtml).