---
layout: post
title: Terminal Seting
date: 2022-12-10
comments: true
external-url:
categories: Ruby
---

PowerShell 配置文件脚本，每次启动之后自动加载

`notepad $PROFILE`

在配置文件里添加以下行：

```shell
oh-my-posh init pwsh --config '$env:POSH_THEMES_PATH\jandedobbeleer.omp.json' | Invoke-Expression
```

重新加载配置文件以使更改生效

`. $PROFILE`

查看所有 themes:

`Get-PoshThemes`

设置选中的 themes：

```shell
oh-my-posh init pwsh --config 'C:\Users\Lenovo\AppData\Local\Programs\oh-my-posh\themes\jandedobbeleer.omp.json' | Invoke-Expression
```

设置随机 themes：

```shell
$theme = Get-ChildItem $env:UserProfile\\AppData\\Local\\Programs\\oh-my-posh\\themes\\ | Get-Random
echo "hello! today's lucky theme is: $theme :)"
oh-my-posh --init --shell pwsh --config $theme.FullName | Invoke-Expression
```

参考链接：

1、[Themes - Oh My Posh](https://ohmyposh.dev/docs/themes)

2、[PowerShell - Oh My Posh](https://updayday.notion.site/1-0-WINDOWS-TERMINAL-PowerShell-Oh-My-Posh-VSCODE-55e13b38fb034d41a122b755f0d47c1b)

3、[ubuntu - oh-my-posh](https://blog.51cto.com/u_15127656/4317154)
