---
layout: post
title: SQL In Excel
date: 2018-10-11
comments: true
external-url:
categories: Office 
---

SQL In Excel

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


    Sql = "SELECT 姓名,成绩 FROM [Sheet1$] WHERE 成绩>=80"
    'Sql语句，查询Sheet1表成绩大于80……姓名和成绩的记录

    Set rst = cnn.Execute(Sql)
    'cnn.Execute()执行SQL语句，始终得到一个新的记录集rst
    '以上是第三步，编写并使用SQL语句


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

    cnn.Close
    '关闭链接

    Set cnn = Nothing
    '释放内存

End Sub

~~~

[示例文件下载地址](链接：https://pan.baidu.com/s/1Zm4di93kNKhOs8HsLNk1Vg)
提取码：15qz

---

## ADO常用连接字符串

~~~
❈　 Access数据库

没有密码保护的Access数据库

Provider=Microsoft.ACE.OLEDB.12.0;Data Source=带路径的Access数据库名称;

有密码保护的Access数据库

Provider=Microsoft.ACE.OLEDB.12.0;Data Source=带路径的Access数据库完整名称;JetOLEDB:Database Password=密码;

❈　 Text文件

Provider=Microsoft.ACE.OLEDB.12.0; Data Source=文本文件路径&'\';Extended Properties=’text;HDR=Yes;FMT=Delimied’;

❈　 SQL Server数据库

Provider =SQLOLEDB;Password=密码;User ID= 用户名; Data Source =SQL数据库服务器名称;Initial Catalog=数据库名称;

❈　 Oracle 数据库

Provider =madaora; PassWord=密码; User ID=用户名; Data Source =Oracle数据库服务器名称;

❈　 FoxPro数据库

Provide=Microsoft.ACE.OLEDB.12.0;User ID=用户名;Data Source=dbf文件路径;Extended Properties=dBASEIV;

❈　 Excel工作簿

03版本Excel

Provider=Microsoft.jet.OLEDB.4.0;Extended Properties=’Excel 8.0;HDR=yes;IMEX=0’;Data Source=带路径的Excel工作簿完整名称

07~16版本Excel

Provider=Microsoft.ACE.OLEDB.12.0;Extended Properties=’Excel 12.0; HDR=yes;IMEX=0’;Data Source=带路径的Excel工作簿完整名称

~~~

---

## 测试链接是否成功

~~~
Sub test()
    Dim cnn As Object
    Set cnn = CreateObject("adodb.connection")
    cnn.Open "provider=microsoft.ace.oledb.12.0;extended properties=excel 12.0;data source=" & ThisWorkbook.FullName
    If cnn.State = 1 Then
        MsgBox "连接成功!" & vbCrLf & "ADO版本为：" & cnn.Version & vbCrLf & "Connection对象提供者名称：" & cnn.provider
        cnn.Close
        Set cnn = Nothing
    Else
        MsgBox "数据库连接失败"
    End If
End Sub


~~~

>State属性返回Connection对象的状态；0是AdStateClosed，表示对象是关闭的；1是AdStateOpen，表示对象是打开的；2是AdStateConnecting，表示对象正在连接等。

Version属性只读，返回Connection对象的版本号；Provider是Connection对象连接数据库提供程序者的名称，当Connection对象关闭时，该属性可读写；否则为只读。


---

[代码来自Excel VBA+ADO+SQL入门教程](https://mp.weixin.qq.com/s?__biz=MzUzODI3ODk1Mw==&mid=100000003&idx=2&sn=1bce514549a940fd0c68a5deecd99180&chksm=7adb6c454dace553434f269529da28870d0047c3f890670dd97d0ebf1bc90cb5351cedd26799&mpshare=1&scene=1&srcid=1012La8yRMpc60NXGwIuMr4f#rd)