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

公式 = =SUMPRODUCT(1/COUNTIF(B2:B81,B2:B81))
>统计合同名称中不重复的单位数量，也就是实际合同总数量
>SUMPRODUCT参数为一个数组时不做乘积，而是求和。

---

2、排名

公式 = SUMPRODUCT((D2<$D$2:$D$8)*1)

---

3、SUMPRODUCT多条件求和的案例讲解


<div class="cloud-tie-wrapper">
<iframe width="800" 
        height="480"
        src="//player.bilibili.com/player.html?aid=11711196&cid=19346720&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>


---
4、高级筛选的条件区域格式

| 范围 | 名称 | 数量 |
| ------: | :------: | ------:|
| >=0.02| 用友网络 | >1000 |
| <=0.05 | 财务部| <2018-09-30 |


---

5、条件格式的公式应用

※ 实现整行记录标识

公式 = $A1="北京无线电测量研究所"

※ 实现间隔行标识

公式 = (MOD(ROW(),2)=1)

※ 满足多条件的数据突出显示

公式 = ($B2>=5000)*($C2>=300)

※ 关键词匹配

公式= FIND ("股份",$A1)

<br>
>注意：规则通过管理进行设置，格式要自行定义


---
6、最常用的30个Excel函数

函数列表

※ 数字处理

1、取绝对值

2、取整

3、四舍五入


※ 判断公式

1）、把公式产生的错误值显示为空

2）、IF多条件判断返回值

※ 统计公式

1）、统计两个表格重复的内容

2）、统计不重复的总人数



※ 求和公式

1）、隔列求和

2）、单条件求和

3）、单条件模糊求和

4）、多条件模糊求和

5）、多表相同位置求和

6）、按日期和产品求和



※ 查找与引用公式

1）、单条件查找公式

2）、双向查找公式

3）、查找最后一条符合条件的记录

4）、多条件查找

5）、指定区域最后一个非空值查找

6）、按数字区域间取对应的值



※ 字符串处理公式

1）、多单元格字符串合并

2）、截取除后3位之外的部分

3）、截取-前的部分

4）、截取字符串中任一段的公式

5）、字符串查找

6）、字符串查找一对多



※ 日期计算公式 

1）、两日期相隔的年、月、天数计算

2）、扣除周末天数的工作日天数


>参考：[Excel精英培训:最常用的30个Excel函数公式](https://mp.weixin.qq.com/s?__biz=MjM5NDYyNzAzNQ==&mid=2652913414&idx=1&sn=0f1ce55dff1142a2b986e54b681d48fc&chksm=bd5073b28a27faa4139587922a762b36456e28090dcbdb38950d9291301c45a104605717de4c&mpshare=1&scene=1&srcid=1001UaMS65oAt9nhYDfS22WS#rd)


>参考[Excel双向查找的9种方法,附送日常工作的20个Excel小技巧）](https://mp.weixin.qq.com/s?__biz=MjM5NTk5NDk0Mg%3D%3D&idx=5&mid=2651539731&sn=824bf439219d1c03ded7e4d2226bcae1)

---