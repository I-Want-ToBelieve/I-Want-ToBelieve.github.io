---
title: 热键脚本语言之AutoHotKey
date: 2017-12-31 14:24:06
tags:
- 教程
- Win10
- AutoHotKey
categories:
- Win10-15063
- 技巧篇
---

- [AutoHotKey官网][AutoHotKey官网]
- 知乎专栏[AutoHotkey 之美](https://zhuanlan.zhihu.com/autohotkey) (AutoHotkey 之美)
- [AutoHotkey中文chm文档](https://sourceforge.net/projects/ahkcn/)
- [AutoHotkey中文在线文档][https://ahkcn.github.io/docs/AutoHotkey.htm]


马上就2018年了.最近为了能在2018年找到一份工作,一直在忙于学习前端的知识.
想想好久都没更新了,所以更新一篇吧,也算是休息一下.

## 热键脚本语言之AutoHotKey

你可以在这看到效果演示视频：`TODO`

## 简介

AutoHotKey是一款免费的、Windows平台下开放源代码的热键脚本语言，是为游戏操纵杆和鼠标创建的热键，是自动按键。也可以通过命令调用系统接口及程序，并创建基于简单语言的图形化界面的执行程序。

简而言之,就是你可以用AutoHotKey来封装你在使用计算机时的频繁操作,然后给他定义热键,当你按下你定义的热键时,这些频繁操作将自动执行.

需要说在前面的是,AutoHotKey是一门脚本语言,有些脚本你直接拿来就可以用,而有些个性化的需求就需要你自己改写代码了.不过不用担心,AutoHotKey的语法非常简单,你肯定可以轻易学会.

## 下载与安装

**下载**

1. 进入[AutoHotKey官网][AutoHotKey官网]
2. 点击绿色的 **Download** 按钮
3. 标题为 **Other Releases** 下的 **AutoHotkey 1.1.* - previously known as AutoHotkey_L**  就是了.点击即可下载.

**安装**

1. 按照[快捷启动之Win+R][Win+R]这篇教程里说的,将下载下来的压缩包解压到 **auxiliaryProgram** 文件夹,就算安装完毕了

**使用**

- 安装好后我们还需要在非系统盘的根目录新建一个名为 **AHKSet** 的文件夹
该文件夹将专门存储后续编写的AHK脚本文件

- 在 **auxiliaryProgram** 文件夹,找到并打开刚才解压出来的子目录 **AutoHotKey**

该目录下应有以下文件:

![AutoHotKeyfl][AutoHotKeyfl]

[AutoHotKeyfl]: <http://oy9dwtsnx.bkt.clouddn.com/autohotkeyfl.png> (AutoHotKeyfl)

其中

第一个是[AutoHotKey官网][AutoHotKey官网]的url文件

第二个是AutoHotKey的英文文档.点击[下载中文文档](https://sourceforge.net/projects/ahkcn/).

第三个是AutoHotKey卸载以及升级的脚本

第四个是一个模板脚本,我们可以复制这个模板脚本到 **AHKSet** 文件夹
也可以通过在 **AHKSet** 文件夹空白处  **<=>**  右键 **<=>** 新建  **<=>**  AutoHotkey Script的方式创建一个空白的脚本.


- 现在我们找到 **AHKSet** 文件夹 **<=>** 并为其新建快捷方式 **<=>** 将AHKSet文件夹的快捷方式重命名为 **AS** 或者 **as** 或者 **ahkset** 都行
**<=>** 重命名后右键选中 **<=>** 发送到  **<=>** 选中lnkSet.

Tips:
别选错了,是选AHKSet文件夹的  **快捷方式** . **其后缀为.lnk**

 做完上步我们就可以通过 **Win+R** 热键  **<=>**  呼出运行窗口  **<=>**  键入上面定义的命令名  **<=>**  回车. 快速的打开我们的autohotkey脚本库了.如果有不知道这是在干嘛的,请移步看看下[这篇教程][WinR]吧.

 现在让我们开始写第一个ahk脚本吧

## 第一个ahk脚本

1. 在 **AHKSet** 文件夹中 **<=>** 右键 **<=>** 新建  **<=>**  AutoHotkey Script  **<=>**  重名为 MoveRunWindow

2. 选中 MoveRunWindow.ahk **<=>** 右键  **<=>** Edit Script **<=>** 然后删除其中的内容

3. 复制以下代码并粘贴到你脚本文档中

```ahk
WindowToCenter(WinTitle)
{
    WinGetPos,,, Width, Height, %WinTitle%
    WinMove, %WinTitle%,, (A_ScreenWidth/2)-(Width/2), (A_ScreenHeight/2)-(Height/2)
    WinSet, Transparent, 220, %WinTitle%
}

#r::

Send, #{r}

WinWait, 运行, , 3
if ErrorLevel
{
    MsgBox, WinWait timed out.
    return
}
else
WindowToCenter(运行)

```

4. 按CTRL+S 保存当前文档 **<=>** 然后再右键选中该脚本 **<=>** 选择 Run Script

5. 现在按 Win+R 试试.




[AutoHotKey官网]: <https://www.autohotkey.com/> (AutoHotKey官网)

[WinR]: <http://floatsyi.com/2017/11/02/%E5%BF%AB%E6%8D%B7%E5%90%AF%E5%8A%A8%E4%B9%8BWin+R/> (快捷启动之Win+R)
