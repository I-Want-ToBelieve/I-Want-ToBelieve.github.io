---
title: '基于 Arch Liunx 的 发行版: Manjaro'
date: 2019-12-07 17:27:11
tags:
- liunx
- arch
- manjaro
---

![manjaro desktop screen](http://r.photo.store.qq.com/psc?/V12iDrZG1mzmnh/uMeul31pGB4ZvQm8Ou4xcQusFzaMQtX5c0lWF3.b9dQ0gdyG**xu7pJP1Ns1qbaRd2mytJizJc5OiZ2jnpiLu2n.3DPccdoc.J7w6ZF9Ors!/r)

[manjaro xfce]: https://manjaro.org/download/official/xfce/
[Rufus]: https://rufus.ie/
[manjaro]: https://manjaro.org/
[manjaro.forum]: https://forum.manjaro.org/
[manjaro.userguide]: https://manjaro.org/support/userguide/
[diskgenius]: http://www.diskgenius.cn/help/index.php?from=dg
## 参考

- [manjaro][]
- [manjaro.forum][]
- [manjaro.userguide][]
- [Rufus]

## 资源

- [manjaro xfce][]
- [Rufus][]
- [diskgenius][]


## 制作 U 盘引导，并硬盘安装 manjaro 与 windows 10 双系统

### 前提条件

- 一个多余的硬盘     （需要被格式化）
- 一个 > 4GB 的 U 盘 （需要被格式化）
- 支持 UEFI 的主板
- 关闭 安全启动 与 快速启动

### 步骤
1. 下载 [manjaro xfce][] minimal 镜像文件并验证文件完整性
2. 下载 U 盘引导写入工具 [Rufus][]
```powershell
scoop bucket add extras
scoop install Rufus
```
3. 使用 [diskgenius][] 将要安装 [manjaro xfce][] 的硬盘快速分区， 设置如下图：
  ![diskgenius 快速分区](http://r.photo.store.qq.com/psc?/V12iDrZG1mzmnh/uMeul31pGB4ZvQm8Ou4xcT19I3WCV*fRmPLfQxeajyi6ofvaSLyDegoi9PkLgt7AJ.J3xLRFAF*Vao.97Mo7XjNLFWgASEbTMH*Rtj9ElMU!/r)
4. 使用 [Rufus][] 将 [manjaro xfce][] minimal 镜像文件写入 U 盘， 设置如下图：
  ![Rufus 写入镜像](http://r.photo.store.qq.com/psc?/V12iDrZG1mzmnh/uMeul31pGB4ZvQm8Ou4xcZ8veDcASaoVEfG0BZSSWfGkdm9yN0QblxXsOIJhJvD8qTKoIXdKSA00JlEK8EeM.dCTFC8rLTSRDEFolKU5MDY!/r)
5. 写入完成后， 重启计算机， 按主板厂商定义的快捷键进入 UEFI 设置界面
  选择从 U 盘启动。
6. 启动后即可进入 manjaro 安装引导界面， 根据 manjaro 安装引导完成安装。

## 安装 yay
```bash
sudo pacman -S yay
```

## 使用中国镜像
```bash
sudo pacman-mirrors -i -c China -m rank
sudo pacman -Syy
```

## 安装 vscode
```bash
yay -S code
```

## 安装 i3wm
```bash
yay -S i3-gaps
```

在 `~/.xinit` 末尾加上 `exec i3`
```bash
echo exec i3 >> ~/.xinit
```


## 安装终端模拟器 alacritty


## 安装 fish shell

## 安装 oh-my-fish

## 安装 neofeh

## 安装 python

### 安装 pip

## 安装 nvm

### 安装 node



## 安装 polybar

## 安装 中文输入法

## 蓝牙

## 安装网易云播放器







