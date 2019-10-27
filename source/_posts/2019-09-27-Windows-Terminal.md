---
title: Windows Terminal
date: 2019-09-27 04:20:27
tags:
- Windows 10
- Terminal
---

![windows-terminal screenshot](http://r.photo.store.qq.com/psb?/V12iDrZG1mzmnh/rmPlL7vfaZsLhZAnI9ch3BEsRyE*Ym1FoMdegS9LTOU!/r/dIMAAAAAAAAA)

## 资源

- [microsoft/terminal](https://github.com/microsoft/terminal/)
- [iTerm2-Color-Schemes](https://github.com/mbadolato/iTerm2-Color-Schemes/tree/master/windowsterminal)

## 前提条件

- 操作系统	Windows 10 版本 18362.0 或更高版本
- 体系结构	ARM64、x64、x86

- [检查你的系统版本](https://docs.microsoft.com/zh-cn/windows/wsl/troubleshooting#check-your-build-number)

## 安装 Windows Terminal (Preview)

- [安装 windows-terminal-preview](https://www.microsoft.com/zh-cn/p/windows-terminal-preview/9n0dx20hk701?activetab=pivot:overviewtab)

## 更换字体与主题并修改启动命令行

**注意: 需要先安装 [scoop](https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop)**

1. 按快捷键 `win + X + A`以管理员权限打开 powershell 终端, 然后执行以下命令, 以下载安装 `Droid Sans Mono for Powerline` 字体(由于这个[bug](https://github.com/microsoft/terminal/issues/633), 只能先用这个字体), 以及 `FuraCode Nerd Font Mono` 字体
    ```powershell
    scoop bucket add nerd-fonts
    sudo scoop install DroidSansMono-NF
    sudo scoop install FiraCode-NF
    ```
2. 按快捷键 `win +  Q` 然后键入 `windows terminal` 并回车, 以运行 `windows terminal`.
3. 选中 `windows terminal` 并按快捷键 `ctrl + ,(逗号)`, 以编辑 `windows terminal` 配置文件: `profiles.json`.
4. 复制以下内容并覆盖 `profiles.json` 文件, 按快捷键 `Ctrl + S` 以保存修改.
```json
{
    "$schema": "https://aka.ms/terminal-profiles-schema",
    "profiles" :
    [
        {
            "acrylicOpacity" : 0.75,
            "closeOnExit" : true,
            "colorScheme" : "Teerb",
            "commandline" : "cmd.exe",
            "cursorColor" : "#FFFFFF",
            "cursorShape" : "bar",
            "fontFace" : "Droid Sans Mono for Powerline",
            "fontSize" : 16,
            "guid" : "{08b5e85b-3615-463d-8df1-70bc4703863f}",
            "historySize" : 9001,
            "icon" : "ms-appdata:///roaming/CMD_32px.png",
            "name" : "CMD",
            "padding" : "0, 0, 0, 0",
            "snapOnInput" : true,
            "startingDirectory" : "%USERPROFILE%",
            "useAcrylic" : true
        },
        {
            "acrylicOpacity" : 0.8,
            "background" : "#1c1c1c",
            "closeOnExit" : true,
            "colorScheme" : "Teerb",
            "commandline" : "powershell.exe",
            "cursorColor" : "#FFFFFF",
            "cursorShape" : "bar",
            "fontFace" : "FuraCode Nerd Font Mono",
            "fontSize" : 14,
            "guid" : "{95e05ea2-6bad-4896-bcdf-a4f96c885cc8}",
            "historySize" : 9001,
            "icon" : "ms-appdata:///roaming/powershell_32px.png",
            "name" : "PowerShell",
            "padding" : "0, 0, 0, 0",
            "snapOnInput" : true,
            "startingDirectory" : "%USERPROFILE%",
            "useAcrylic" : true
        },
        {
            "acrylicOpacity" : 0.85,
            "closeOnExit" : false,
            "colorScheme" : "Teerb",
            "commandline" : "wsl.exe -- cd ~;source ~/.profile;fish",
            "cursorColor" : "#FFFFFF",
            "cursorShape" : "bar",
            "fontFace" : "Droid Sans Mono for Powerline",
            "fontSize" : 12,
            "guid" : "{78e390db-1bff-4533-9d7c-20f53d8bafa1}",
            "historySize" : 9001,
            "icon" : "ms-appdata:///roaming/ubuntu_32px.png",
            "name" : "Ubuntu",
            "padding" : "0, 0, 0, 0",
            "snapOnInput" : true,
            "useAcrylic" : true
        },
        {
            "guid": "{c6eaf9f4-32a7-5fdc-b5cf-066e8a4b1e40}",
            "hidden": false,
            "name": "Ubuntu-18.04",
            "source": "Windows.Terminal.Wsl"
        },
        {
            "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
            "hidden": false,
            "name": "Azure Cloud Shell",
            "source": "Windows.Terminal.Azure"
        }
    ],
    "schemes" :
    [
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
    "globals" :
    {
        "alwaysShowTabs" : true,
        "defaultProfile" : "{78e390db-1bff-4533-9d7c-20f53d8bafa1}",
        "initialCols" : 120,
        "initialRows" : 30,
        "keybindings" :
        [
            {
                "command" : "closeTab",
                "keys" :
                [
                    "ctrl+w"
                ]
            },
            {
                "command" : "newTab",
                "keys" :
                [
                    "ctrl+t"
                ]
            },
            {
                "command" : "newTabProfile0",
                "keys" :
                [
                    "ctrl+shift+1"
                ]
            },
            {
                "command" : "newTabProfile1",
                "keys" :
                [
                    "ctrl+shift+2"
                ]
            },
            {
                "command" : "newTabProfile2",
                "keys" :
                [
                    "ctrl+shift+3"
                ]
            },
            {
                "command" : "newTabProfile3",
                "keys" :
                [
                    "ctrl+shift+4"
                ]
            },
            {
                "command" : "newTabProfile4",
                "keys" :
                [
                    "ctrl+shift+5"
                ]
            },
            {
                "command" : "newTabProfile5",
                "keys" :
                [
                    "ctrl+shift+6"
                ]
            },
            {
                "command" : "newTabProfile6",
                "keys" :
                [
                    "ctrl+shift+7"
                ]
            },
            {
                "command" : "newTabProfile7",
                "keys" :
                [
                    "ctrl+shift+8"
                ]
            },
            {
                "command" : "newTabProfile8",
                "keys" :
                [
                    "ctrl+shift+9"
                ]
            },
            {
                "command" : "nextTab",
                "keys" :
                [
                    "ctrl+tab"
                ]
            },
            {
                "command" : "openSettings",
                "keys" :
                [
                    "ctrl+,"
                ]
            },
            {
                "command" : "prevTab",
                "keys" :
                [
                    "ctrl+shift+tab"
                ]
            },
            {
                "command" : "scrollDown",
                "keys" :
                [
                    "ctrl+shift+down"
                ]
            },
            {
                "command" : "scrollDownPage",
                "keys" :
                [
                    "ctrl+shift+pgdn"
                ]
            },
            {
                "command" : "scrollUp",
                "keys" :
                [
                    "ctrl+shift+up"
                ]
            },
            {
                "command" : "scrollUpPage",
                "keys" :
                [
                    "ctrl+shift+pgup"
                ]
            },
            {
                "command" : "switchToTab0",
                "keys" :
                [
                    "alt+1"
                ]
            },
            {
                "command" : "switchToTab1",
                "keys" :
                [
                    "alt+2"
                ]
            },
            {
                "command" : "switchToTab2",
                "keys" :
                [
                    "alt+3"
                ]
            },
            {
                "command" : "switchToTab3",
                "keys" :
                [
                    "alt+4"
                ]
            },
            {
                "command" : "switchToTab4",
                "keys" :
                [
                    "alt+5"
                ]
            },
            {
                "command" : "switchToTab5",
                "keys" :
                [
                    "alt+6"
                ]
            },
            {
                "command" : "switchToTab6",
                "keys" :
                [
                    "alt+7"
                ]
            },
            {
                "command" : "switchToTab7",
                "keys" :
                [
                    "alt+8"
                ]
            },
            {
                "command" : "switchToTab8",
                "keys" :
                [
                    "alt+9"
                ]
            }
        ],
        "requestedTheme" : "system",
        "showTabsInTitlebar" : true,
        "showTerminalTitleInTitlebar" : true
    }
}
```




