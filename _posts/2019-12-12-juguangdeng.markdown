---
layout: post
title: Excel 聚光灯效果的实现
date: 2019-12-12
comments: true
external-url:
categories: Office 
---

Excel 高亮显示选中行列：聚光灯效果

※ 1. 条件格式设置公式： 

~~~
=OR(CELL("row")=ROW())
=OR(CELL("col")=COLUMN()) 
=(CELL("row")=ROW())+(CELL("col")=COLUMN())
~~~

※ 2. VBA 工作表选择 Worksheet SelectionChange 加入代码

~~~
Private Sub Worksheet_SelectionChange(ByVal Target As Range)
On Error Resume Next
If Application.CutCopyMode = xlCopy Or Application.CutCopyMode = xlCut Then Exit Sub
ActiveSheet.Calculate
End Sub
~~~

>条件格式设置时，范围要设置整个数据区域;

>文件保存格式为 .xlsm


※ 3. 纯VBA 实现方式：

~~~

Private Sub Worksheet_SelectionChange(ByVal Target As Range)
With Target
     .Parent.Cells.Interior.ColorIndex = xlNone
     .EntireRow.Interior.Color = RGB(230, 230, 250)
     .EntireColumn.Interior.Color = RGB(250, 235, 215)
End With
End Sub

~~~

>[颜色代码参考](http://tool.oschina.net/commons?type=3)
