---
layout: w
title: 'The Package Manager for Windows: choco and scoop'
date: 2019-12-29 13:50:51
tags:
- choco
- scoop
---

[安装 windows 包管理工具: scoop]: https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop
[scoop]: https://github.com/lukesampson/scoop
[choco]: https://github.com/chocolatey/choco

## 参考
- [安装 windows 包管理工具: scoop][]

## 资源
- [scoop][]
- [choco][]

<!-- more -->

## 安装 scoop
- [安装 windows 包管理工具: scoop][]

## 安装 choco
1. 按快捷键 `Win + X + A` 打开 powershell 终端窗口
2. 请在 powershell 终端窗口执行以下命令, 以设置 choco 安装目录:
    ```powershell
    $env:ChocolateyInstall='X:\Support\Choco' # choco 安装目录, 你可以自行修改为合适的路径.
    [Environment]::SetEnvironmentVariable('ChocolateyInstall', $env:ChocolateyInstall, 'Machine')
    ```
3. 关闭当前终端窗口, 再次按快捷键 `Win + X + A` 打开 powershell 终端窗口, 执行以下命令, 以安装 choco:
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
    ```
4. 执行 `choco -v` 以验证安装. -->
