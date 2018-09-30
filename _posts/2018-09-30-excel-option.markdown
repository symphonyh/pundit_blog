---
layout: post
title: Excel 使用技巧
date: 2018-09-30
comments: true
external-url:
categories: Office 
---



---

1、统计不重复项的个数

公式 = SUMPRODUCT(1/COUNTIF(B2:B292,B2:B292))
>统计合同名称中不重复的单位数量，也就是实际合同总数量
>SUMPRODUCT参数为一个数组时不做乘积，而是求和。

---

2、高级筛选的条件区域格式

| 范围 | 名称 | 数量 |
| ------: | :------: | ------:|
| >=0.02| 用友网络 | >1000 |
| <=0.05 | 财务部| <2018-09-30 |


---


