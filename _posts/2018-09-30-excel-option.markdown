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

如果是多列不重复：

公式 =SUMPRODUCT(1/COUNTIF(A2:A81,A2:a81,B2:B81,B2:B81))

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

---

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

11、一个关键字查找筛选对应的多行数据 `INDEX+SMALL+IF` 万金油函数

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

14、当数字变 E+ , 一个？让它现原形！

`Ctrl + 1 `设置单元格格式 - 自定义 - 输入数字 `0 `

>如果输入 `0000000` 当0的个数大于整数位，会用0在数字前补齐

还可以输入`？`和`#` 达到同样效果，区别是：

- 当0的个数大于整数位时，会以0补齐位数

- 当？的个数大于整数位时，会以空格补齐位数

- 当#的个数大于整数位时，不补。

---

15、按单元格颜色求和

※ step1：定义名称，为提取颜色值做准备

公式 - 定义名称 ，在定义名称窗口中输入名称 mycolor（可以自定义），然后在下面引用来源中输入公式：


=GET.CELL(63,Sheet2!B2)&T(NOW())

>公式说明：

>Get.cell(63,单元格) 可以获取单元格填充颜色值

>&T(NOW()) 实现表格在更新时定义名称取值也可以更新

※ step2：获取颜色值

在C列和E列分别输入公式 =mycolor，即可获取B列和D列的单元格填充色。


※ step3：剩下的交给sumif函数吧

=SUMIF(C:C,E2,B:B)

---

16、制作二级联动下拉

※ step1：设置数据源区域。就是把手机名称和型号整理成如下图格式备用，存放的位置随意;

※ step2：批量定义名称。选取手机名称和型号区域后，公式选项卡 - 定义的名称组 - **根据所选内容创建**，选取窗口上的“首行”复选框;

※ step3：设置数据有效性。选取型号列，打开数据有效性窗口，在来源中输入=indirect(D5)


---

17、实现自动到期提醒

要求：离到期日30天内行填充红色，60天内填充黄色。要求可以修改G2:G3的期间，提醒色会自动更新

※ step1、添加到期天数列，计算出离还款还有多少天。

公式 =D2-TODAY()

※ step2、添加辅助表，可以用来动态调整提醒的天数。

15表示15天内，45表示45天内。

※ step3、选取表格（标题行不选），开始 - 条件格式 - 新建规则。然后进行如下设置：

- 类型：使用公式确定要设置格式的单元格

- 设置格式框中输入公式 =$E2<$G$2（按E列到期日判断，所在E前要加$）

- 点格式按钮，设置填充色为红色。

※ step4、按※ step3方法，再添加一个规则。公式为=$E2<$G$3，格式设置为黄色。

※ step5、开始 - 条件格式 - 管理规则，在规则管理窗口中，把30天内规则提升到最上面。

设置完成！



>16-17参考：[Excel表格的精选39个技巧](https://mp.weixin.qq.com/s?__biz=MjM5NDYyNzAzNQ==&mid=2652912144&idx=1&sn=70b9a4c5bd63b39bc3bcf005de563cfb&chksm=bd5076a48a27ffb2b73c90e199f81c437dfa487ce8af72bf9e9da2443e129cf072283214faff&mpshare=1&scene=1&srcid=1004HRwvrMVtPcTKG7CjGG9v#rd)

---

18、Mlookup函数来了

=Mlookup(查找内容，查找区域,返回值所在的列数,第N个)

语法说明：

查找内容：除了单个值外，还可以选取多个单元格，进行多条件查找。

查找区域：同VLOOKUP

返回值的在列数：同VLOOKUP

第N个：值为1就返回第1个符合条件的，值为2就返回第2个符合条件的....当值为0值时，返回最后1个符合条件的值，值为-1时返回所有查找结果并用逗号连接。

举例：

※ 查找第2次电视的进货数量。

=Mlookup(A11,A2:D8,4,2)

※ 查找电视的最后一次入库数量

=Mlookup(A11,A2:D8,4,0)

※ 查找47寸电视的第1次进货数量。

=Mlookup(A11:B11,A2:D8,4,1)

※ 实现筛选功能。

=Mlookup($B$10:$B$11,$A$1:$D$8,4,A14)

※ 实现多结果查找功能。（把所有符合条件结果用逗号连接起来）

=MLOOKUP(A11,B$1:C$8,2,-1)

>18 参考：[Mlookup函数来了](https://mp.weixin.qq.com/s?__biz=MjM5NDYyNzAzNQ==&mid=2652912073&idx=1&sn=deca355c82a286defed9f17bce4f2c05&chksm=bd50757d8a27fc6b8bc512f697d48677bfd6b2f70fe434e0cc7f416f3c5c36794fcc9ea2b457&mpshare=1&scene=1&srcid=1004rjYRGah9meoYlPJyBn5U#rd)

---

19、获取文件路径

文件-信息-打开文档位置


---

20、通过批注添加图片

在制作产品介绍表或员工信息表时，常需要添加产品图片和员工照片，这时用批注插入图片是最好的选择。

选取批注 - 右键“设置批注格式” - **颜色** - 填充效果 - 图片 -选择图片

---


21、利用批注完成快速合并两列文字

先插入一批注，然后复制多列数据，再选取批注按ctrl+v粘贴，然后再复制批注文字粘贴到表格中即可。

>注意：很多同学粘贴批注无效，是因为要点选批注边缘来选取批注，不要让批注进入文字编辑状态。


---

22、每页打印标题行

如果想在打印时每一页都显示标题，页面布局 - 打印标题 - 首端标题行：选取要显示的行

---

23、同时修改多个工作表

按shift或ctrl键选取多个工作表，然后在一个表中输入内容或修改格式，所有选中的表都会同步输入或修改。这样就不必逐个表修改了。

---

24、恢复未保存文件

打开路径：C:\Users\Administrator\AppData\Roaming\Microsoft\Excel\ ，在文件夹内会找到的未保存文件所在的文件夹


---

25、选择性粘贴的计算（把所有数据进行计算）

常用的把财务数据转为万元版

※ step1： 在一个单元格输入1000,并且复制这个单元格 Ctrl + C


※ step2：选择数据区域全部数据


※ step3：选择性粘贴，选 `除` 确定即可。


---

26、高亮显示选中行

※ step1：条件格式设置公式：=OR(CELL("row")=ROW())

※ step2：VBA 工作表选择 Worksheet SelectionChange 加入代码

~~~

Private Sub Worksheet_SelectionChange(ByVal Target As Range)
ActiveSheet.Calculate
End Sub

~~~

>条件格式设置时，范围要设置整个数据区域


---


