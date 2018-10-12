---
layout: post
title: SQL In Excel
date: 2018-10-11
comments: true
external-url:
categories: Office 
---

## Excel 中正确使用SQL的姿势

~~~
Sub DoSql_Execute1()

    Dim cnn As Object, rst As Object

    Dim Mypath As String, Str_cnn As String, Sql As String

    Dim i As Long

    Set cnn = CreateObject("adodb.connection")

    '以上是第一步，后期绑定ADO

    
    Mypath = ThisWorkbook.FullName

    If Application.Version < 12 Then

        Str_cnn = "Provider=Microsoft.jet.OLEDB.4.0;Extended Properties=Excel 8.0;Data Source=" & Mypath

    Else

        Str_cnn = "Provider=Microsoft.ACE.OLEDB.12.0;Extended Properties=Excel 12.0;Data Source=" & Mypath

    End If

    cnn.Open Str_cnn

    '以上是第二步，建立链接

    '

    Sql = "SELECT 姓名,成绩 FROM [Sheet1$] WHERE 成绩>=80"

    'Sql语句，查询Sheet1表成绩大于80……姓名和成绩的记录

    Set rst = cnn.Execute(Sql)

    'cnn.Execute()执行SQL语句，始终得到一个新的记录集rst

    '以上是第三步，编写并使用SQL语句

    '

    [d:e].ClearContents

    '清空[d:e]区域的值

    For i = 0 To rst.Fields.Count - 1

    '利用fields属性获取所有字段名，fields包含了当前记录有关的所有字段,fields.count得到字段的数量

    '由于Fields.Count下标为0，又从0开始遍历，因此总数-1

        Cells(1, i + 4) = rst.Fields(i).Name

    Next

    Range("d2").CopyFromRecordset rst

    '使用单元格对象的CopyFromRecordset方法将rst内容复制到D2单元格为左上角的单元格区域

    '以上是第四步，将SQL查询结果和字段名写入表格指定区域

    '

    cnn.Close

    '关闭链接

    Set cnn = Nothing

    '释放内存

End Sub

~~~

[示例文件下载地址](链接：https://pan.baidu.com/s/1Zm4di93kNKhOs8HsLNk1Vg 
)
提取码：15qz