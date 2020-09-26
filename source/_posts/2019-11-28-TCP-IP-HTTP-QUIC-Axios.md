---
title: 'TCP/IP, HTTP, QUIC, Axios'
date: 2019-11-28 22:37:19
tags:
- tcp/ip
- http
- axios
---
> 我看了下旁边的计算机， 又看了看手下的键盘， 还有眼前的显示器.
键盘是一个输入， 输入的是一个数据结构， 计算机是一个函数， 输出是一个数据结构， 被显示器解析.
我的眼睛接收到的是一个数据结构， 我的大脑是一个函数， 我的手指敲击键盘， 完成了一次输入.
------ 这样的闭环，它有美妙的名字： 人机交互.

[MDN web docs: http]: https://developer.mozilla.org/zh-CN/docs/Web/HTTP
[MDN web docs: Cookies]: https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Cookies
[MDN web docs: HTTP Headers]: https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers
[MDN web docs: HTTP Methods]: https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods
[MDN web docs: HTTP Status]: https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status
[本站开始支持 QUIC]: https://halfrost.com/quic_start/
[如何看待 HTTP/3 ？ ------@zhihu]: https://www.zhihu.com/question/302412059/answer/533223530
[HTTP/3详解]: https://http3-explained.haxx.se/zh/
[axios]: https://github.com/axios/axios
## 参考

- [MDN web docs: http][]
- [MDN web docs: Cookies][]
- [MDN web docs: HTTP Headers][]
- [MDN web docs: HTTP Methods][]
- [MDN web docs: HTTP Status][]
- [TCP-IP详解卷一：协议]
- [图解HTTP]
- [本站开始支持 QUIC][]
- [如何看待 HTTP/3 ？ ------@zhihu][]
- [HTTP/3详解][]

## 资源

- [axios][]

<!-- more -->

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
- [MDN web docs: http][]
看了下 《图解HTTP》， 以下是少许提炼

客户端与服务器通过 HTTP 协议对话.
HTTP 是对 TCP 协议的封装.

### HTTPS

客户端与服务器通过 HTTPS 协议进行**加密**对话.
HTTPS 是对 SSL 与 TCP 协议的封装.
通常，HTTP 直接和 TCP 通信。当使用 SSL 时，则演变成先和 SSL 通信，再由 SSL 和 TCP 通信.

### 请求

请求报文由 请求头 与 请求体 组成。


#### 请求头

- [MDN web docs: HTTP Headers][]

请求头由 请求行， 通用首部字段（请求与响应通用的字段）， 请求首部字段与实体首部字段组成
所谓字段就是一种 key-value 型数据结构.
请求行由 请求方法 , 请求地址与HTTP版本号组成
例： GET /index.html HTTP/1.1

##### 请求方法
请求方法常用的有以下几种：
- GET 获取资源
- POST 提交实体主体（就是请求体）
- PUT 传输文件（在 RESTful  API 中是提出修改请求）
- DELETE 删除 （在 RESTful  API 中是提出删除请求）

- HEAD 获取响应头
- OPTIONS：询问指定 url 支持的方法

#### 请求体
请求体一般是你要提交的 json 数据

### 响应
响应报文由 响应头 与 响应体 组成。

#### 响应头
响应头由 状态行， 通用首部字段（请求与响应通用的字段）， 响应首部字段与实体首部字段组成
状态行由 响应结果的状态码，原因短语和 HTTP 版本号组成
例： HTTP/1.1 200 OK

##### 状态码

- [MDN web docs: HTTP Status][]

1XX Informational（信息性状态码） 接收的请求正在处理
2XX Success（成功状态码） 请求正常处理完毕
3XX Redirection（重定向状态码） 需要进行附加操作以完成请求
4XX Client Error（客户端错误状态码） 服务器无法处理请求
5XX Server Error（服务器错误状态码） 服务器处理请求出错

常用的响应码如下：
- 200 OK 表示从客户端发来的请求在服务器端被正常处理了
- 204 No Content 返回的响应报文中不含实体的主体部分, 换言之， 没有响应数据.
- 206 Partial Content 表示服务器成功处理了客户端的范围请求

- 301 Moved Permanently
  永久性重定向， 该状态码表示请求的资源已被分配了新的 URI
  希望用户以后应使用资源现在所指的 URI。
  甚至将url尾部的 `/` 去掉 都会响应301
  如 `http://example.com/sample/` 改为 `http://example.com/sample`
- 302 Found 临时性重定向。该状态码表示请求的资源已被分配了新的 URI， 希望
  用户（本次）能使用新的 URI 访问。
- 303 See Other 同 302 Found， 但 303 状态码明确表示客户端应当采用 GET 方法获取资源
>当原先为 POST 请求，却得到响应状态码为 301、302、303 的重定向响应时，几乎所有的浏览器都会把
随后的 POST 请求改成 GET，并删除请求报文内的主体。
301、302 标准是禁止将 POST 方法改变成 GET 方法的，但实际使用时大家都会这么做。
- 304 Not Modified
  该状态码表示客户端发送附带条件的请求 2 时，服务器端允许请求访问资源，但未满足条件的情况。
  304 状态码返回时，不包含任何响应的主体部分。
  304 虽然被划分在 3XX 类别中，但是和重定向没有关系。
> 附带条件的请求是指采用 GET 方法的请求报文中包含 If-Match，If-ModifiedSince，If-None-Match，If-Range，If-Unmodified-Since 中任一首部。
- 307 Temporary Redirect 临时重定向。
  该状态码与 302 Found 有着相同的含义。
  尽管 302 标准禁止 POST 变换成 GET，但实际使用时大家并不遵守。
  307 会遵照浏览器标准，不会从 POST 变成 GET。
  但是，对于处理响应时的行为，每种浏览器有可能出现不同的情况。

- 400 Bad Request
  该状态码表示请求报文中存在语法错误。
  当错误发生时，需修改请求的内容后再次发送请求。
  另外，浏览器会像 200 OK 一样对待该状态码
- 401 Unauthorized
  该状态码表示发送的请求需要有通过 HTTP 认证（BASIC 认证、DIGEST 认证）的认证信息。
  另外若之前已进行过 1 次请求，则表示用户认证失败。
  返回含有 401 的响应必须包含一个适用于被请求资源的 WWWAuthenticate 首部用以质询（challenge）用户信息。
  当浏览器初次接收到 401 响应，会弹出认证用的对话窗口。
- 403 Forbidden
  该状态码表明对请求资源的访问被服务器拒绝了。
  服务器端没有必要给出拒绝的详细理由，但如果想作说明的话，可以在实体的主体部分
- 404 Not Found
  该状态码表明服务器上无法找到请求的资源。
  除此之外，也可以在服务器端拒绝请求且不想说明理由时使用。

- 500 Internal Server Error
  该状态码表明服务器端在执行请求时发生了错误。
  也有可能是 Web应用存在的 bug 或某些临时的故障。
- 503 Service Unavailable
  该状态码表明服务器暂时处于超负载或正在进行停机维护，现在无法处理请求。
  如果事先得知解除以上状况需要的时间，最好写入 RetryAfter 首部字段再返回给客户端。


> 状态码有可能和状况不一致
不少返回的状态码响应都是错误的，但是用户可能察觉不到这点。
比如 Web 应用程序内部发生错误，状态码依然返回 200 OK，这种
情况是属于编写应用的人员未规范使用状态码导致的。
#### 响应体

响应体一般是你要获取的 json 数据

### 缓存， Cookie， 跨域 CORS， HTTP/1.x 中的连接管理， web 安全

- [MDN web docs: http][]

## QUIC 与 HTTP/3

- [如何看待 HTTP/3 ？ ------@zhihu][]
- [HTTP/3详解][]
- [本站开始支持 QUIC][]

## axios

Promise based HTTP client for the browser and node.js

- [axios][]



