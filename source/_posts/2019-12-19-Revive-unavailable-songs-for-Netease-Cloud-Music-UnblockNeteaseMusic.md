---
title: 'Revive unavailable songs for Netease Cloud Music: UnblockNeteaseMusic'
date: 2019-12-19 04:36:51
tags:
- UnblockNeteaseMusic
---

[nondanee/UnblockNeteaseMusic]: https://github.com/nondanee/UnblockNeteaseMusic
[oldj/SwitchHosts]: https://github.com/oldj/SwitchHosts
[javascript 开发环境搭建(windows 10)]: https://github.com/FloatingShuYin/development-environment-manual/blob/master/javascript.md
[Securely build, share and run any application, anywhere: docker]: https://floatsyi.com/2019/12/29/Securely-build-share-and-run-any-application-anywhere-docker/
## 参考
- [javascript 开发环境搭建(windows 10)][]
- [Securely build, share and run any application, anywhere: docker][]

## 资源
- [nondanee/UnblockNeteaseMusic][]
- [oldj/SwitchHosts][]

## 步骤
UWP 版本使用 host 转发的方法：
1. 参考 [javascript 开发环境搭建(windows 10)][]， 安装 node 与 scoop.
或者 参考 [Securely build, share and run any application, anywhere: docker][] 安装 docker

2. 按快捷键 `win + x + a` 以管理员权限运行 powershell， 并执行以下命令以允许将 UWP 应用请求转发到 localhost
```powershell
checknetisolation loopbackexempt -a -n="1F8B0F94.122165AE053F_j2p0p5q0044a6"
```

3. 执行 `scoop bucket add extras;scoop install switchhosts` 以下载安装 [oldj/SwitchHosts][]

4. 执行 `sudo start "$env:SCOOP/apps/switchhosts/current/SwitchHosts!.exe"` 以管理员权限打开 switchhosts， 并新建以下规则
```hosts
# netease music
127.0.0.1 music.163.com
127.0.0.1 interface.music.163.com
```

5. 执行 `ping music.163.com` 获取 cdn 服务器的 ip 地址

6. 将此 `npx @nondanee/unblockneteasemusic -p 80 -f 59.111.181.35` 命令中的 59.111.181.35 替换为上一步获取的 ip 地址并执行

**推荐使用** docker: `docker run --name unblockneteasemusic -e NODE_ENV=production -d -p 80:8080 nondanee/unblockneteasemusic -f 59.111.181.35`

或者 docker-compose -f ./unblockneteasemusic.yml up -d
unblockneteasemusic.yml:
```yml
version: '3'

services:
  unblockneteasemusic:
    image: nondanee/unblockneteasemusic
    environment:
      NODE_ENV: production
    ports:
      - 80:8080
    entrypoint: node app.js -f 59.111.181.35
```

7. 打开网易云音乐 uwp 以验证转发服务工作正常
