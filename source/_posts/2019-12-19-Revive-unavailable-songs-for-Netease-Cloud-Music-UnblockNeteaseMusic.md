---
title: 'Revive unavailable songs for Netease Cloud Music: UnblockNeteaseMusic'
date: 2019-12-19 04:36:51
tags:
- UnblockNeteaseMusic
---

[nondanee/UnblockNeteaseMusic]: https://github.com/nondanee/UnblockNeteaseMusic
[oldj/SwitchHosts]: https://github.com/oldj/SwitchHosts
[javascript 开发环境搭建(windows 10)]: https://github.com/FloatingShuYin/development-environment-manual/blob/master/javascript.md

## 参考
- [javascript 开发环境搭建(windows 10)][]

## 资源
- [nondanee/UnblockNeteaseMusic][]
- [oldj/SwitchHosts][]

## 步骤
UWP 版本使用 host 转发的方法：
1. 参考 [javascript 开发环境搭建(windows 10)][]， 安装 node 与 scoop.

2. 按快捷键 `win + x + a` 以管理员权限运行 powershell， 并执行以下命令以允许将 UWP 应用请求转发到 localhost
```powershell
checknetisolation loopbackexempt -a -n="1F8B0F94.122165AE053F_j2p0p5q0044a6"
```

3. 执行 `scoop bucket add extras;scoop install switchhosts` 以下载安装 [oldj/SwitchHosts][]

4. 执行 `sudo start "$env:SCOOP/apps/switchhosts/current/SwitchHosts!.exe"` 以管理员权限打开 switchhosts， 并新建以下规则
```hosts
127.0.0.1 music.163.com
127.0.0.1 interface.music.163.com
```

5. 执行 `ping music.163.com` 获取 cdn 服务器的 ip 地址

6. 将此 `npx @nondanee/unblockneteasemusic -p 80 -f 59.111.181.60` 命令中的 59.111.181.60 替换为上一步获取的 ip 地址并执行

7. 打开网易云音乐 uwp 以验证转发服务工作正常
