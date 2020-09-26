---
title: 'an in-memory database that persists on disk: redis'
date: 2020-01-17 03:33:06
tags:
- in-memory database
- redis
---
[redis]: https://github.com/antirez/redis
[redis.io]: https://redis.io/
[Redis 菜鸟教程]: https://www.runoob.com/redis/redis-tutorial.html
[windows subsystem archliunx]: https://floatsyi.com/2020/01/17/windows-subsystem-archliunx/

## 参考
- [windows subsystem archliunx][]
- [redis.io][]
- [Redis 菜鸟教程][]


## 资源
- [redis][]

<!-- more -->

## 安装
安装 wsl2 archliunx
请参考  [windows subsystem archliunx][]

在 wsl2 中安装 [redis][]
```bash
sudo pacman -S redis
```

验证安装
```bash
redis-server --version
redis-cli --version
```

## 扩展阅读
看书吧！！
- 《redis 开发与运维》
- 《redis 深度历险核心原理与应用实践》

官网文档： https://redis.io/documentation
