---
title: 'TCP/IP, HTTP, QUIC, Axios'
date: 2019-11-28 22:37:19
tags:
- tcp/ip
- http
- axios
---

## 参考

[MDN web docs: http]: https://developer.mozilla.org/zh-CN/docs/Web/HTTP

## 资源

- [MDN web docs: http][]

## TCP/IP
看了下 <<TCP-IP详解卷一：协议>>, 非常详(ku)细(zao)
只领悟到一些比较抽象的东西, 没时间去实践, 所以暂时弃之, 有空玩玩 wireshark 实践下.
不过对理解 HTTP 协议应该是足够了.


### Wireshark
安装
```powershell
scoop install Wireshark
```
现在没时(xing)间(qu)学网络分析, 先放着.

## HTTP

客户端与服务器通过 HTTP 协议对话.
HTTP 是对 TCP 协议的封装.

### HTTPS

客户端与服务器通过 HTTPS 协议进行**加密**对话.
HTTPS 是对 SSL 与 TCP 协议的封装.
通常，HTTP 直接和 TCP 通信。当使用 SSL 时，则演变成先和 SSL 通信，再由 SSL 和 TCP 通信.

####



