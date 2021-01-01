---
title: 'node 包管理工具: npm 与 yarn'
date: 2019-10-30 21:41:15
tags:
- npm
- yarn
- 包管理
---

[yarn 官网]: <https://yarnpkg.com/zh-Hans/>
[npm 官网]: <https://www.npmjs.com/>

## 资源
- [npm 官网][]
- [yarn 官网][]

## 安装
- [node 版本管理与 npm 仓库镜像源](https://floatsyi.com/2019/09/27/node-%E7%89%88%E6%9C%AC%E7%AE%A1%E7%90%86%E4%B8%8E-npm-%E4%BB%93%E5%BA%93%E9%95%9C%E5%83%8F%E6%BA%90/)

安装 yarn
```bash
npm install yarn -g
```

## 代理

设置代理
```bash
#npm
npm config set proxy http://127.0.0.1:1080
npm config set https-proxy http://127.0.0.1:1080
# yarn
yarn config set proxy http://127.0.0.1:1080
yarn config set https-proxy http://127.0.0.1:1080
```

删除代理
```bash
#npm
npm config delete proxy
npm config delete https-proxy
# yarn
yarn config delete proxy
yarn config delete https-proxy
```

## 镜像

ref: https://npm.taobao.org/mirrors

nvm
```bash
export NVM_NODEJS_ORG_MIRROR=http://npm.taobao.org/mirrors/node
export NVM_IOJS_ORG_MIRROR=http://npm.taobao.org/mirrors/iojs
```

```bash
npm config set registry https://registry.npm.taobao.org -g
npm config set disturl https://npm.taobao.org/dist -g
npm config set electron_mirror https://npm.taobao.org/mirrors/electron/ -g
npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/ -g
npm config set phantomjs_cdnurl https://npm.taobao.org/mirrors/phantomjs/ -g
```

```bash
yarn config set registry https://registry.npm.taobao.org -g
yarn config set disturl https://npm.taobao.org/dist -g
yarn config set electron_mirror https://npm.taobao.org/mirrors/electron/ -g
yarn config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/ -g
yarn config set phantomjs_cdnurl https://npm.taobao.org/mirrors/phantomjs/ -g
```
