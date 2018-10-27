---
layout: post
title: Everything
date: 2018-10-27
comments: true
external-url:
categories: Office 
---


Everything CommonTools


语法：

| 符号 | 解释 | 举例 | 解释 |
|:-----------------| :-----------------| :----------------- |:----------------- |
| 空格 |	与	 | li chao | 文件(夹)名中既含li又含chao |
| `| `  |或	 | 1.txt`|`2.txt	|文件名含1或2的txt文件 |
| `！`|非 |	*.txt !b | 文件名不含b的txt文件 |
| `< >` | 提高优先级,类似于数学的() | file:<1 `|` 2 > |文件名含1或2的文件(夹) |
| `""` |特殊字符串	 |"foo bar"	| 如果没有引号会认为是逻辑与 |

---
通配符：

`* `匹配0-∞个任意字符

例如：a*.txt 匹配形如”ab.txt” “abbb.txt”

`?` 匹配1个任意字符

例如：a??.txt 匹配形如”abc.txt” “aaa.txt”

---

修饰符：

`case:` 匹配大小写

`file:`只匹配文件

`folder:`只匹配文件夹

`path:`匹配路径和文件名

`regex:`正则表达式

`ww: wholeword:`全字匹配

---

函数：


`dc:<date>` 搜索特定创建日期的目标

例如：

     *.txt dc:lastyear 去年创建的txt文件
     *.txt dc:2010-2012

`dm:<date>`搜索特定修改日期的目标

`dupe:` 搜索重复目标

例如：

     dupe:text
     dupe:!text

`empty:` 搜索空文件夹

`ext:<list>` 搜索指定后缀的目标 用分号分隔

例如：

     file:<ext:bmp;txt> bmp和txt文件

>函数允许使用 `= < > !`逻辑符号

---
<br>

正则表达式：

<table>
<thead>
<tr>
<th>目标</th>
<th>语法</th>
</tr>
</thead>
<tbody>
<tr>
<td>找到所有c:\windows目录及其下任意子目录的txt文件</td>
<td>c:\windows*.txt</td>
</tr>
<tr>
<td>找出所有bmp和jpg文件</td>
<td>*.bmp | *.jpg</td>
</tr>
<tr>
<td>找出所有名为download文件夹下的所有avi文件</td>
<td>download\ .avi</td>
</tr>
<tr>
<td>找出所有名字中含.tx的文件夹</td>
<td>folder:.tx</td>
</tr>
<tr>
<td>搜索空txt文件</td>
<td>*.txt file:size:0</td>
</tr>
<tr>
<td>搜索所有大于1MB的常见图像文件</td>
<td>&lt;<em>.bmp|</em>.jpg|<em>.png|</em>.tga&gt; size:&gt;1mb</td>
</tr>
<tr>
<td>找到所有c:\windows目录下的txt文件</td>
<td>regex:c:\windows\[^]*.txt</td>
</tr>
<tr>
<td>列出所有c:\windows的N级子目录</td>
<td>regex:c:\windows\[<sup>]*(\[</sup>]*){N}$</td>
</tr>
<tr>
<td>列出所有c:\windows的N级子目录下的txt文件</td>
<td>regex:c:\windows\[<sup>]*(\[</sup>]*){N}.txt$</td>
</tr>
<tr>
<td>查找所有全字匹配1.txt的文件</td>
<td>ww:1.txt</td>
</tr>
<tr>
<td>查找wi开头的h文件和cpp文件</td>
<td>file:&lt;wi<em>.h|wi</em>.cpp&gt; or wi* &lt;ext:h|cpp&gt;</td>
</tr>
<tr>
<td>XXX第N集.rmvb”，XXX是电视剧名，N是数字</td>
<td>regex:.*第[0-9]+集</td>
</tr>
<tr>
<td>连续的RAR压缩包 XXXX.partN.rar，XXXX是压缩包名，N是数字</td>
<td>regex:.*part[0-9]+.rar</td>
</tr>
<tr>
<td>连续的ZIP压缩包 XXXX.zN</td>
<td>regex:.*.z[0-9]+</td>
</tr>
<tr>
<td>搜索所有纯中文目标</td>
<td>regex:<sup>[</sup>0-9a-z]*$</td>
</tr>
<tr>
<td>搜索带中文字符的目标</td>
<td>regex:<sup>.*[</sup>!-~]+.*$</td>
</tr>
</tbody>
</table>

---

[节选自简书：Everything工具使用](https://www.jianshu.com/p/51534f6ecf48)