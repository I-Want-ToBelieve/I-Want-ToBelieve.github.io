---
title: 使用 MutationObserver 监听 DOM 变更
date: 2019-11-01 15:40:53
tags:
- MutationObserver
---

[不要翻译 github 上的代码]: https://greasyfork.org/zh-CN/scripts/376658-%E4%B8%8D%E8%A6%81%E7%BF%BB%E8%AF%91github%E4%B8%8A%E7%9A%84%E4%BB%A3%E7%A0%81/code
[MutationObserver]: https://developer.mozilla.org/zh-CN/docs/Web/API/MutationObserver
[lodash debounce 源码]: https://github.com/lodash/lodash/blob/15e1557b2a97c8bbee22d873832d90ed3ba50ba7/debounce.js
[github]: https://github.com/

## 资源

- [不要翻译 github 上的代码][]
- [MutationObserver][]
- [lodash debounce 源码][]
- [github][]

## [不要翻译 github 上的代码][]

因为需要经常逛 [github][] 查阅文档, 而文档大多都是英文
还好 chrome 浏览器自带的网页翻译用起来不错
只是把代码也给翻译了, 就很难受
所以呢, 就写了这个脚本来避免 chrome 浏览器翻译代码
起初呢, 逻辑非常简单
chrome 之所以翻译代码是因为 github 上文档的 `<pre><code></code></pre>` 没有写全
推测是 markdown 解析器的问题
不过无所谓了, 只需要遍历页面中所有的 `<code></code>` 元素补全就可以了
但是呢, 后来又遇到点问题:
因为 github 网站呢, 是个 SPA(单页面应用),
脚本只能在首次页面加载完成后执行一次, 完全管不到随后的 DOM 变更
于是呢, 我就思考了一下我只要在 DOM 即将变更时得到通知, 并在 DOM 变更完后
抢在 chrome 翻译前把 `<code></code>` 元素补全就好了
如下:
我首先呢, 在 `document` 上添加了一个点击事件监听器
这样呢, 我就可以知道 DOM 有可能要发生变更了
但是呢, 我没办法知道 DOM 何时开始变更完成,
所以呢, 我就只好用 `setInterval(()=>{}, 50)` 过量执行
并在 `setTimeout(()=>{}, 5000)` 后停止执行
```js
document.addEventListener('click', function () {
  const int = setInterval(()=>{ doNotTranslateCode() }, 50)
  setTimeout(()=>{ clearInterval(int) }, 5000)
})
```
后来呢
用着也挺不错, 就是比较看脸, 页面加载太长超过 5s 就不行了, 而且比较浪费性能
然后就突然想到 chrome 是怎么在 DOM 更新后翻译新加载的 DOM 内容的?
是不是有什么 API 可以监听 DOM 变更然后通知我呢

## [MutationObserver][]

后来一查
果然有这个东西, 叫 MutationObserver
以下节选一段使用 MutationObserver 的实现:
```js
  // debug log
const isDev = true
const log = (...args) => {
  isDev && console.log(...args)
}
const _ = {}
_.debounce = function (func, wait) { // debounce code}

const githubTV = document.querySelector('body')
const npmTV = document.querySelector('body')
const isGitHub =
  window.location.href.search(/github.com/i) !== -1 && !!githubTV
const isNPM = window.location.href.search(/npmjs.com/i) !== -1 && !!npmTV

// MutationObserver option
const option = {
  childList: true,
  subtree: true
}

let time = 0

const doNotTranslate = function (mutations, observer) {
  // 处于过于频繁的 DOM 变更时, 暂停监听 50ms, 并放弃累积的未处理的变更事件
  if (time >= 20) {
    observer.disconnect()
    observer.takeRecords()
    time = 0
    // 在 50ms 后重启监听
    setTimeout(function () {
      isGitHub && observer.observe(githubTV, option)
      isNPM && observer.observe(npmTV, option)
    }, 50)
  }

  // 不要翻译文件名与目录
  doNotTranslateFilenamesAndDirectories()
  // 不要翻译代码内容页
  doNotTranslateCodeContentPages()
  // 不要翻译代码
  doNotTranslateCode()
  // 不要翻译标题
  doNotTranslateTitle()

  time++
  log(`第${time}次执行: doNotTranslate`)
}

const MutationObserver =
  window.MutationObserver ||
  window.WebKitMutationObserver ||
  window.MozMutationObserver
const mo = new MutationObserver(_.debounce(doNotTranslate, 50))

isGitHub && mo.observe(githubTV, option)
isNPM && mo.observe(npmTV, option)
```

>给我带来更多的感触是
我深深的感觉到了我处境的悲哀
我本可以不必节省这些翻阅词典的时间
我本可以不必放弃这一次次的学习英语的场景
但我必须这样做, 我必须在深知这是饮鸩止渴的情况下饮鸩止渴
我因为我之前处境的狭隘,浪费了太多的时间, 因此没有太多的选择给我了
这其实是一个恶性循环
我为此痛苦的寻求 break
