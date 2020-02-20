---
title: 'A JavaScript library for building user interfaces: React'
date: 2020-02-02 01:53:04
tags:
- react
- react-hook
- react-router
---

[prettier stylelint husky lint-staged 与 create-react-app typescript 样板集成]: https://floatsyi.com/2020/01/19/prettier-stylelint-husky-lint-staged-%E4%B8%8E-create-react-app-typescript-%E6%A0%B7%E6%9D%BF%E9%9B%86%E6%88%90/
[react]: https://github.com/facebook/react
[react-router]: https://github.com/ReactTraining/react-router
[react-testing-library]: https://github.com/testing-library/react-testing-library
[react-testing-library docs]: https://testing-library.com/docs/react-testing-library/intro
[jest]: https://github.com/facebook/jest
[react docs]: https://zh-hans.reactjs.org/docs/getting-started.html
[react docs: hook]: https://zh-hans.reactjs.org/docs/hooks-intro.html
[react docs: test]: https://zh-hans.reactjs.org/docs/testing.html
[react router docs]: https://reacttraining.com/react-router/web/example/basic
[jest docs]: https://jestjs.io/docs/en/getting-started
[2020-01-21-使用-react-app-rewired-扩展-cra-样板的配置文件]: https://floatsyi.com/2020/01/21/%E4%BD%BF%E7%94%A8-react-app-rewired-%E6%89%A9%E5%B1%95-cra-%E6%A0%B7%E6%9D%BF%E7%9A%84%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6/

> 我知道我自己的知识缺陷，但是当我需要它们的时候我可以比较快的掌握它们。
这些缺陷不会让我的知识和经验贬值，我可以做好很多事情，比如说：当我需要某些技术的时候学会它们。
--- Dan Abramov

[Dan Abramov(React 核心开发，Redux 作者) 谈他不懂的技术](https://zhuanlan.zhihu.com/p/53587347)

## 参考

- [prettier stylelint husky lint-staged 与 create-react-app typescript 样板集成][]
- [2020-01-21-使用-react-app-rewired-扩展-cra-样板的配置文件][]
- [react docs][]
- [react docs: hook][]
- [react docs: test][]
- [react router docs][]
- [react-testing-library docs][]
- [jest docs][]

## 资源

- [react][]
- [react-router][]
- [react-testing-library][]
- [jest][]

## 前言

最近加入了一个志愿者组织，参与学习观网站的前端开发。
(说好的转型后端呢？emmm...学习观网站后端选型选的 java，我尝试配了下开发环境，
结果使用 maven 打包项目的时候， 终端报错刷屏至少刷了三分钟...哇，都不带停的，真的厉害，报错都这么啰嗦！
看样子是 maven 依赖项的问题， 要知道 maven 的配置文件可是 xml 写的，啊真是啰嗦！
又想起很久以前被 java 那啰嗦的写法支配的恐惧了... 直接劝退。
如果能改成 node 栈比如说用 nestjs 也许还可以插下手， java 就别想了...)
咳咳， 前端开发我之前一直是用的 vue, 很少有认真用过 react
这次呢， 学习观网站开发用的是 react 的技术栈， 所以这篇文章呢，就是为了能全面掌控这个前端项目
而对 react 的一次全面整理了。

> 记住方法， 而不是答案， 盯紧月亮， 而不是手指。

有 vue 的经验转 react 其实是非常快速的， 就是一段通读官方文档的时间， 一周而已。

## create-react-app

这个东西就是 react 官方的脚手架了，生成项目模板用的
参考:

- [prettier stylelint husky lint-staged 与 create-react-app typescript 样板集成][]
- [2020-01-21-使用-react-app-rewired-扩展-cra-样板的配置文件][]

## [react][]

参考: [react docs][]

## hook

参考: [react docs: hook][]

## [react-router][]

参考: [react router docs][]

## [react-testing-library][] and [jest][]

参考:
- [react docs: test][]
- [react-testing-library docs][]
- [jest docs][]

## react-redux

...

## 扩展阅读

- [Personal blog by Dan Abramov. I explain with words and code.](https://overreacted.io/)
- [将 React 作为 UI 运行时](https://overreacted.io/zh-hans/react-as-a-ui-runtime/)
- [useEffect 完整指南](https://overreacted.io/zh-hans/a-complete-guide-to-useeffect/#tldr)
- [技术周刊 2019-11-12：JavaScript 年度安全报告，React 介绍并发模式](https://zhuanlan.zhihu.com/p/91501173)
- [React Hooks(一): From Redux to Hooks](https://zhuanlan.zhihu.com/p/83552786)
- [React Hooks(二): useCallback 之痛](https://zhuanlan.zhihu.com/p/98554943)
- [React Hooks(三): 并发之道，初入协程](https://zhuanlan.zhihu.com/p/99977314)
- [Hooks 时代的 React 状态管理方案](https://zhuanlan.zhihu.com/p/68434464)
- [正确掌握React 生命周期(Lifecycle)](https://zhuanlan.zhihu.com/p/24926575)
- [9102，作为前端必须知道 hook 怎么玩了](https://juejin.im/post/5d00a67cf265da1b8a4f156f)
- [rehooks/awesome-react-hooks](https://github.com/rehooks/awesome-react-hooks)
- [react-use/react-use](https://github.com/streamich/react-use)
- [gragland/usehooks](https://github.com/gragland/usehooks)
- [2019年了，整理了N个实用案例帮你快速迁移到React Hooks](https://juejin.im/post/5d594ea5518825041301bbcb#heading-1)
- [精读《React Hooks 最佳实践》](https://zhuanlan.zhihu.com/p/81752821)
- [(译) 在 React Hooks 中如何请求数据？](https://juejin.im/post/5c98fb35518825157172acc6)
- [React Suspense + 自定义Hook开启数据请求新方式](https://juejin.im/post/5dc953235188250c6c41683e)
- [精读《Hooks 取数 - swr 源码》](https://zhuanlan.zhihu.com/p/91228591)
- [SWR 源码浅析](https://juejin.im/post/5de72afbe51d45584f536f57)


