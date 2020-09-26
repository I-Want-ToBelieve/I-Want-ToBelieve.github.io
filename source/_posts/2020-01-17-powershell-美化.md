---
title: powershell 美化
date: 2020-01-17 03:55:15
tags:
- powershell
- 美化
---

[Windows-Terminal]: https://floatsyi.com/2019/09/27/Windows-Terminal/
[microsoft/terminal]: https://github.com/microsoft/terminal/
[告别 Windows 终端的难看难用，从改造 PowerShell 的外观开始]: https://sspai.com/post/52868
[5 个 PowerShell 主题，让你的 Windows 终端更好看]: https://sspai.com/post/52907
[iTerm2-Color-Schemes]: https://github.com/mbadolato/iTerm2-Color-Schemes/tree/master/windowsterminal

## 参考
- [Windows-Terminal][]
- [告别 Windows 终端的难看难用，从改造 PowerShell 的外观开始][]
- [5 个 PowerShell 主题，让你的 Windows 终端更好看][]

## 资源
- [microsoft/terminal][]
- [iTerm2-Color-Schemes][]

<!-- more -->


## 安装
安装及配置终端模拟器 [microsoft/terminal][]
请参考 [Windows-Terminal][]

安装 oh-my-posh 和 posh-git
```powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
```

安装 colortool
```
scoop install colortool
```

clone [iTerm2-Color-Schemes][]
```powershell
cd ~
git clone --depth 1 https://github.com/mbadolato/iTerm2-Color-Schemes.git
```

## 美化
```
code $PROFILE
```

Microsoft.PowerShell_profile.ps1
```powershell
Import-Module posh-git
Import-Module oh-my-posh
Set-Culture en-US
Set-Theme Sorin
clear
# Paradox
```

修改主题
```
cd ~\iTerm2-Color-Schemes\schemes
colortool -d ./Tomorrow.itermcolors
```
