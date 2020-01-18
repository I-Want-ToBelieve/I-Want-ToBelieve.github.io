---
title: Windows Terminal
date: 2019-09-27 04:20:27
tags:
- Windows 10
- Terminal
---

![windows-terminal screenshot](http://r.photo.store.qq.com/psb?/V12iDrZG1mzmnh/rmPlL7vfaZsLhZAnI9ch3BEsRyE*Ym1FoMdegS9LTOU!/r/dIMAAAAAAAAA)

[The-Package-Manager-for-Windows-choco-and-scoop]: https://floatsyi.com/2019/12/29/The-Package-Manager-for-Windows-choco-and-scoop/

## 参考
- [The-Package-Manager-for-Windows-choco-and-scoop][]

## 资源

- [microsoft/terminal](https://github.com/microsoft/terminal/)
- [iTerm2-Color-Schemes](https://github.com/mbadolato/iTerm2-Color-Schemes/tree/master/windowsterminal)

## 前提条件

- 操作系统	Windows 10 版本 18362.0 或更高版本
- 体系结构	ARM64、x64、x86

- [检查你的系统版本](https://docs.microsoft.com/zh-cn/windows/wsl/troubleshooting#check-your-build-number)

## 安装 Windows Terminal (Preview)

参考 [安装 windows-terminal-preview](https://www.microsoft.com/zh-cn/p/windows-terminal-preview/9n0dx20hk701?activetab=pivot:overviewtab)

或者参考 [The-Package-Manager-for-Windows-choco-and-scoop][]
```
sudo choco install microsoft-windows-terminal --yes
```

## 更换字体与主题并修改启动命令行

**注意: 需要先安装 [scoop](https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop)**

1. 按快捷键 `win + X + A`以管理员权限打开 powershell 终端, 然后执行以下命令, 以下载安装 `Droid Sans Mono for Powerline` 字体(由于这个[bug](https://github.com/microsoft/terminal/issues/633), 只能先用这个字体), 以及 `FuraCode Nerd Font Mono` 字体
    ```powershell
    scoop bucket add nerd-fonts
    sudo scoop install DroidSansMono-NF
    sudo scoop install FiraCode
    ```
2. 按快捷键 `win +  Q` 然后键入 `windows terminal` 并回车, 以运行 `windows terminal`.
3. 选中 `windows terminal` 并按快捷键 `ctrl + ,(逗号)`, 以编辑 `windows terminal` 配置文件: `profiles.json`.
4. 复制以下内容并覆盖 `profiles.json` 文件, 按快捷键 `Ctrl + S` 以保存修改.
<!-- "commandline" : "wsl.exe -- cd ~;source ~/.profile;fish", -->
```json
// To view the default settings, hold "alt" while clicking on the "Settings" button.
// For documentation on these settings, see: https://aka.ms/terminal-documentation

{
  "$schema": "https://aka.ms/terminal-profiles-schema",

  "defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
  "initialCols" : 140,
  "initialRows" : 30,
  "profiles": [
    {
      // Make changes here to the powershell.exe profile
      "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
      "acrylicOpacity": 0.9,
      "fontSize": 12,
      "fontFace": "Fira Code",
      "cursorShape": "underscore",
      "historySize": 9001,
      "useAcrylic" : true,
      "name": "Windows PowerShell",
      "colorScheme": "Tomorrow Night",
      "commandline": "powershell.exe",
      "hidden": false,
      "startingDirectory": null
    },
    {
      // Make changes here to the cmd.exe profile
      "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
      "name": "cmd",
      "commandline": "cmd.exe",
      "hidden": false
    },
    {
      "guid": "{a5a97cb8-8961-5535-816d-772efe0c6a3f}",
      "hidden": false,
      "name": "Arch",
      "source": "Windows.Terminal.Wsl"
    },
    {
      "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
      "hidden": false,
      "name": "Azure Cloud Shell",
      "source": "Windows.Terminal.Azure"
    }
  ],

  // Add custom color schemes to this array
  "schemes": [
    {
      "name": "Tomorrow Night",
      "black": "#000000",
      "red": "#cc6666",
      "green": "#b5bd68",
      "yellow": "#f0c674",
      "blue": "#81a2be",
      "purple": "#b294bb",
      "cyan": "#8abeb7",
      "white": "#ffffff",
      "brightBlack": "#000000",
      "brightRed": "#cc6666",
      "brightGreen": "#b5bd68",
      "brightYellow": "#f0c674",
      "brightBlue": "#81a2be",
      "brightPurple": "#b294bb",
      "brightCyan": "#8abeb7",
      "brightWhite": "#ffffff",
      "background": "#1d1f21",
      "foreground": "#c5c8c6"
    },
    {
      "name": "Tomorrow",
      "black": "#000000",
      "red": "#c82829",
      "green": "#718c00",
      "yellow": "#eab700",
      "blue": "#4271ae",
      "purple": "#8959a8",
      "cyan": "#3e999f",
      "white": "#ffffff",
      "brightBlack": "#000000",
      "brightRed": "#c82829",
      "brightGreen": "#718c00",
      "brightYellow": "#eab700",
      "brightBlue": "#4271ae",
      "brightPurple": "#8959a8",
      "brightCyan": "#3e999f",
      "brightWhite": "#ffffff",
      "background": "#ffffff",
      "foreground": "#4d4d4c"
    },
    {
      "name": "Teerb",
      "black": "#1c1c1c",
      "red": "#d68686",
      "green": "#aed686",
      "yellow": "#d7af87",
      "blue": "#2e8fff",
      "purple": "#d6aed6",
      "cyan": "#8adbb4",
      "white": "#d0d0d0",
      "brightBlack": "#595959",
      "brightRed": "#d68686",
      "brightGreen": "#aed686",
      "brightYellow": "#e4c9af",
      "brightBlue": "#86aed6",
      "brightPurple": "#d6aed6",
      "brightCyan": "#b1e7dd",
      "brightWhite": "#efefef",
      "background": "#262626",
      "foreground": "#d0d0d0"
    }
  ],

  // Add any keybinding overrides to this array.
  // To unbind a default keybinding, set the command to "unbound"
  "keybindings": []
}
```

## 添加到鼠标右键菜单
下载 wget
```
scoop install wget
```

下载 terminal-box-fill.ico
```
cd ~
wget.ps1 https://raw.githubusercontent.com/FloatingShuYin/FloatingShuYin.GitHub.io/hexo/terminal-box-fill.ico
```

新建 window.terminal.reg 文件
修正其中路径
```reg
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\Background\shell\wt]
@="Open Windows Terminal here"
"Icon"="X:\\terminal-box-fill.ico"

[HKEY_CLASSES_ROOT\Directory\Background\shell\wt\command]
@="S:\\Users\\doublethink\\AppData\\Local\\Microsoft\\WindowsApps\\wt.exe"
```

双击 window.terminal.reg 执行


