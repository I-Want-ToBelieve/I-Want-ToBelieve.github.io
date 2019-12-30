---
title: 'Securely build, share and run any application, anywhere: docker'
date: 2019-12-29 14:24:53
tags:
- docker
---
[The Package Manager for Windows: choco and scoop]: https://floatsyi.com/2019/12/29/The-Package-Manager-for-Windows-choco-and-scoop/
[Docker — 从入门到实践]: https://docker_practice.gitee.io/zh-cn/
[Docker]: https://github.com/topics/docker
[docker.com]: https://www.docker.com/
## 参考
- [The Package Manager for Windows: choco and scoop][]
- [Docker — 从入门到实践][]
- [docker.com]

## 资源
- [Docker][]

## 安装
1. 首先要安装 choco: [The Package Manager for Windows: choco and scoop][]

2. 按 `win + x + a` 快捷键打开 powershell 终端窗口

3. 执行以下命令， 以下载安装 docker-for-windows
```powershell
choco install docker-for-windows --yes
```
4. 执行以下命令， 以验证安装
```powershell
docker --version;docker-compose --version;docker-machine --version;
```

## 看书吧！！
> This is the way

- [Docker — 从入门到实践][]
- [docker.com]
