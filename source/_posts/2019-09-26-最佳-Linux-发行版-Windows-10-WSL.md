---
title: 最佳 Linux 发行版 Windows 10(WSL)
date: 2019-09-26 13:51:13
tags:
- WSL
- 最佳 Linux 发行版 Windows 10
---

![WSL in Windows Terminal](http://r.photo.store.qq.com/psb?/V12iDrZG1mzmnh/rmPlL7vfaZsLhZAnI9ch3BEsRyE*Ym1FoMdegS9LTOU!/r/dIMAAAAAAAAA)

[安装 wsl]: https://docs.microsoft.com/zh-cn/windows/wsl/install-win10
[microsoft/terminal]: https://github.com/microsoft/terminal/
[Ubuntu 清华大镜像使用帮助]: https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/
[repository file generator]: https://mirrors.ustc.edu.cn/repogen/
[apt-mirror-updater]: https://github.com/xolox/python-apt-mirror-updater
[apt-smart]: https://github.com/martin68/apt-smart
[oh-my-fish]: https://github.com/oh-my-fish/oh-my-fish
[Homebrew-on-Linux]: https://docs.brew.sh/Homebrew-on-Linux
[fish shell 主题]: https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md
## 资源
- [关于 wsl](https://docs.microsoft.com/zh-cn/windows/wsl/about)
- [wsl.exe 命令行参数](https://docs.microsoft.com/zh-cn/windows/wsl/reference)
- [安装 wsl][]
- [microsoft/terminal][]
- [Ubuntu 清华大镜像使用帮助][]
- [repository file generator][]
- [apt-smart][]
- [apt-mirror-updater]
- [oh-my-fish][]
- [fish shell 主题][]

## 安装 wsl 及其必要条件

- [安装 wsl][]

## 安装 Windows Terminal

- [安装 Windows Terminal](https://floatsyi.com/2019/09/27/Windows-Terminal/)

## 添加包管理工具 apt 的镜像源

1. 按快捷键 `win +  Q` 然后键入 `wsl` 并回车, 以运行 `wsl`.
2. 选中 `wsl` 并执行以下命令以备份 `sources.list`(仓库源配置文件)
```bash
cd /etc/apt
sudo mv sources.list sources.list.bak
```
3. 下载 sources.list
注意: 下载地址在这里获取 [repository file generator][]
```bash
cd /etc/apt
sudo curl https://mirrors.ustc.edu.cn/repogen/conf/ubuntu-https-4-bionic -o sources.list
```

4. 更新
```bash
sudo apt update
sudo apt upgrade
```

5. 安装 pip3
```bash
sudo apt install python3-pip
```

6. 执行以下命令,以下载安装 [apt-smart][]
```bash
pip3 install apt-smart
```

7. 执行以下命令, 以验证安装:
```bash
apt-smart -V
```

8. 执行以下命令, 以使用最佳的可用镜像(不一定可信, 最好自己 `apt-smart -l` 权衡一下, 然后 `apt-smart -c the_best_mirror_url` 以应用)
```bash
apt-smart -a
```

### 更新索引

```bash
apt-smart -u
```

## 包管理工具 brew

### 前提条件

安装 build-essential curl file git 以及 ruby

```bash
sudo apt install build-essential curl file git ruby
```

### 安装 [Homebrew-on-Linux][]

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
```

### 添加 brew 路径到环境变量

```bash
test -d ~/.linuxbrew && eval $(~/.linuxbrew/bin/brew shellenv)
test -d /home/linuxbrew/.linuxbrew && eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
test -r ~/.bash_profile && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile
echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.profile
```

### hello world

```bash
brew install hello
```

## 安装 fish shell

```bash
brew install fish
```

**安装完成后关闭当前终端, 然后按快捷键 `win +  Q` 然后键入 `Windows Terminal` 并回车, 以运行 `Windows Terminal`.**

### 安装 [oh-my-fish][]
1. 选中 Windows Terminal, 并执行以下命令, 以安装[oh-my-fish][]

```fish
curl -L https://get.oh-my.fish | fish
```

#### 安装 [fish-plugin-linuxbrew](https://github.com/liamdawson/fish-plugin-linuxbrew.git)

[fish-plugin-linuxbrew](https://github.com/liamdawson/fish-plugin-linuxbrew.git) 是为 fish shell 创建的 linuxbrew 的插件, 作用是将 linuxbrew 的所在路径暴露在 fish shell 的环境变量中, 以满足在 fish shell 中调用 brew 的需求.

```fish
omf install https://github.com/liamdawson/fish-plugin-linuxbrew.git
```

#### 安装 [fish shell 主题][]

执行以下命令, 以下载安装 bobthefish 主题, 并启用 theme_powerline_fonts 与 theme_nerd_fonts, 然后将 theme_color_scheme 改为 base16.

```fish
omf install bobthefish
set -g theme_powerline_fonts yes;set -g theme_nerd_fonts yes;set -g theme_color_scheme base16
```

更多主题相关设置请查看 [fish shell 主题][]

#### 更换 fish shell 关键字主题
在终端窗口键入 `fish_config` 以使用默认浏览器打开 fish web 配置页面
```fish
fish_config
```

#### node 版本管理与 npm 仓库镜像源

- [node 版本管理与 npm 仓库镜像源 (wsl)](https://floatsyi.com/2019/09/27/node-%E7%89%88%E6%9C%AC%E7%AE%A1%E7%90%86%E4%B8%8E-npm-%E4%BB%93%E5%BA%93%E9%95%9C%E5%83%8F%E6%BA%90/#%E5%9C%A8%20liunx(wsl/mac)%20%E4%B8%8B%E4%BD%BF%E7%94%A8%20brew%20%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7%E7%9A%84%E8%BF%9B%E8%A1%8C%E5%AE%89%E8%A3%85)
