---
layout: post
title: Excel 使用技巧
date: 2018-09-30
comments: true
external-url:
categories: Office 
---


## Excel 


1、统计不重复项的个数

公式 =SUMPRODUCT(1/COUNTIF(B2:B81,B2:B81))
>统计合同名称中不重复的单位数量，也就是实际合同总数量
>SUMPRODUCT参数为一个数组时不做乘积，而是求和。

---

2、排名

公式 = SUMPRODUCT((D2<$D$2:$D$8)*1)+1

或

公式 = RANK(A2,($A$2:$A$4）


公式 = RANK(A2,($A$2:$A$4,$C$2:$C$4))

>在（）中用逗号连接多个区域

---

3、实现自动编号，档筛选和隐藏时重新自动编号

公式 = SUBTOTAL(103,B$2:B2) 

---

4、SUMPRODUCT多条件求和的案例讲解


<div class="cloud-tie-wrapper">
<iframe width="800" 
        height="480"
        src="//player.bilibili.com/player.html?aid=11711196&cid=19346720&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>


---
5、高级筛选的条件区域格式

| 范围 | 名称 | 数量 |
| ------: | :------: | ------:|
| >=0.02| 用友网络 | >1000 |
| <=0.05 | 财务部| <2018-09-30 |


---

6、条件格式的公式应用

※ 实现整行记录标识

公式 = $A1="北京无线电测量研究所"

※ 实现间隔行标识

公式 = (MOD(ROW(),2)=1)

※ 满足多条件的数据突出显示

公式 = ($B2>=5000)*($C2>=300)

※ 关键词匹配

公式 = FIND ("股份",$A1)

<br>
>注意：规则通过管理进行设置，格式要自行定义




---

7、如何同时显示日期和星期？

自定义格式:  `yyyy-y-d aaaa` 

---

8、自动生成报表目录并添加超链接

※ step1：`Ctrl + F3`在弹了的窗口中输入名称`getsh`, 在引用位置输入公式：

~~~
引用位置 = MID(GET.WORKBOOK(1),FIND("]",GET.WORKBOOK(1))+1,99)&T(NOW())
~~~

※ step2：在单元格输入公式并下拉即可生成工作表的目录。

~~~
公式 = IFERROR(HYPERLINK("#"&INDEX(getsh,ROW(A2))&"!a1",INDEX(getsh,ROW(A2))),"")
~~~

>这里的名称用的是`getsh`，公式都是在目录页输入的

---

9、数据验证和条件格式结合使用突出显示目标数据

※ step1：在H6设置数据验证列表

※ step2：需要突出显示的数据，设置条件格式 公式 = $A3=$H$6

类似的还可以：

~~~
公式 =A1<>""
公式 =AND($C3="女"，YEAR($D3)>1980)
~~~

>参考：[Excel技巧精选](https://mp.weixin.qq.com/s?__biz=MzA5NTI5NzUyNw==&mid=2666972091&idx=1&sn=a177d23a8d9f23f3ca13e60cae88b177&mpshare=1&scene=1&srcid=1002iFIJEWTOx7xBPLyZuH8g#rd)                                    


10、不改变数据源实现二级联动下拉菜单


<div class="cloud-tie-wrapper">
<iframe width="800" 
        height="480"
        src="//player.bilibili.com/player.html?aid=11712829&cid=19348975&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>
<br>
提示：

※ 主要公式 = OFFSET(B$1,MATCH(G1,A:A,)-1,,COUNTIF(A:A,G1))

※ 数据-删除重复项

※ 取消合并单元格快速填充： F5 定位 - 选空值 - 输入第一个空单元格的取值公式（例如：=A2）- Ctrl + Enter

※ excel中合并单元格快速拉序号，输入公式 =MAX($A$1:A1)+1


>参考：[百度链接：取消合并单元格实现快速填充](https://jingyan.baidu.com/article/a681b0de7b0c3b3b18434632.html)

>本文内容的 13 合并单元格的取消和每行填充相同内容 提供了另一种解决方案！

---
11、一个关键字查找筛选对应的多行数据 `index+small+if` 万金油函数

<div class="cloud-tie-wrapper">
<iframe width="800" 
        height="480"
        src="//player.bilibili.com/player.html?aid=8160452&cid=13420534&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>
<br>

=INDEX(A:A,SMALL(IF(B$2:B$17=G$1,ROW($2:$17),99),ROW(A1)))

=INDEX(C:C,<font color="#DC143C">SMALL(</font><font color="#6495ED">IF(B$2:B$17=G$1,<font color="#DAA520">ROW($2:$17)</font>,999)</font>,<font color="#DC143C">ROW(A1))</font>)

>[点击下载示例文件，   提取码`6w1q` ](https://pan.baidu.com/s/1ZXNePGwH7nrOhNkD-c--9A)

>扩展：[Excel双向查找的9种方法](https://mp.weixin.qq.com/s?__biz=MjM5NTk5NDk0Mg%3D%3D&idx=5&mid=2651539731&sn=824bf439219d1c03ded7e4d2226bcae1)

---

12、报价表文件，不等行的合并单元格对应数据快速求和

※ step1：选中求和列

※ step2：

= SUM( C2:$C$12 )- SUM( D3:$D$12 )

= SUM(数据首行：$数据尾行) - SUM(求和列次行：$求和列次行)

※ step3：Ctrl + Enter

>NC报价表涉及并发数和单价不适合

---

13、合并单元格的取消和每行填充相同内容

公式 = LOOKUP（"座", $D$3:D3)

>主要为VLOOKUP查找扫清道路，去掉合并单元格

---
