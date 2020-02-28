---
title: 'Vegetarian friendly state for React: easy-peasy'
date: 2020-02-28 14:56:34
tags:
- state
- react
---

[Hooks 时代的 React 状态管理方案]: https://zhuanlan.zhihu.com/p/68434464
[easy-peasy]: https://github.com/ctrlplusb/easy-peasy
[apollo-client]: https://github.com/apollographql/apollo-client
[react-state-patterns]: https://github.com/mcclayton/react-state-patterns
[hookstate]: https://github.com/avkonst/hookstate
[unstated-next]: https://github.com/jamiebuilds/unstated-next
[react-state-patterns]: https://github.com/mcclayton/react-state-patterns
[react-hooks-global-state]: https://github.com/dai-shi/react-hooks-global-state
[constate]: https://github.com/diegohaz/constate
[use-profunctor-state]: https://github.com/staltz/use-profunctor-state
[overmind]: https://github.com/cerebral/overmind
[overstated]: https://github.com/fabiospampinato/overstated
[ayanami]: https://github.com/LeetCode-OpenSource/ayanami
[flooks]: https://github.com/nanxiaobei/flooks
[redux]: https://github.com/reduxjs/redux
[mobx]: https://github.com/mobxjs/mobx
[mobx-state-tree]: https://github.com/mobxjs/mobx-state-tree

## 参考
- [Hooks 时代的 React 状态管理方案][]

## 资源
- [easy-peasy][]
- [apollo-client][]

## 关于前端项目全局状态管理库的选型(react)
参考 [Hooks 时代的 React 状态管理方案][]

### 纯 Hooks 的实现
[react-state-patterns][]
[hookstate][]
[unstated-next][]
[react-state-patterns][]
[react-hooks-global-state][]
[constate][]

### 比较奇怪的实现
[use-profunctor-state][]

### 先定义 model，再以 Hooks 的方式消费的实现
- [easy-peasy][]
- [overmind][]
- [overstated][]
- [ayanami][]
- [flooks][]

### 老牌的实现
- [redux][]
- [mobx][]
- [mobx-state-tree][]

### GraphQL的实现
- [apollo-client][]

## 抉择
纯 hook 的实现过于简单,基本上是直接基于 react context api,基本没有模块的实现, 仅仅是单一的状态树.
而老牌的如 [redux][] 则过于复杂, Flux 的概念其实非常不错, 而且基于此的生态十分健壮, 但样板代码又实在是太多了, 显得非常啰嗦.

所以只能在 [easy-peasy][]  [overmind][] [overstated][]  [ayanami][]  [flooks][] 中选一个了.
[ayanami][] 和 [overmind][] 其实都挺不错, 但是都有一个缺点, 引入了其他概念.
如 [ayanami][] 就是基于 rxjs 的实现. 我想喜欢 rxjs 的团队应该会喜欢这个方案.

[flooks][] 去中心化的确不错, 但基于字符串的 api 将会与 typescript 的类型支持进行艰难的斗争
我看了源码, 作者完全放弃了这方面的努力. 羸弱的类型支持, 将使 typescript 形同虚设.

而 [overstated][] 如果没有 [easy-peasy][] 我就选他了

[easy-peasy][] 基于 [redux][] 与 immer .
前者, 使我们能够直接拥有 [redux][] 的繁荣生态, 而不必接纳 [redux][] 啰嗦的样板代码.
后者, 使我们以 Mutable 的形式, 完成 Immutable 的操作.
更高的抽象, 简单的概念, 均衡.

而如果要用 GraphQL 的话, 集请求与状态管理于一身的 [apollo-client][] 将是不二之选.

