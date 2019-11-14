---
title: bable-jest
date: 2019-11-14 15:28:34
tags:
- bable
- jest
- bable-jest
---

[bable-jest]: https://www.npmjs.com/package/babel-jest
[cross-env]: https://github.com/kentcdodds/cross-env
[JavaScript compiler: Babel]: https://floatsyi.com/2019/11/13/JavaScript-compiler-Babel/

## 参考

- [JavaScript compiler: Babel][]

## 资源

- [bable-jest][]
- [cross-env][]


## [bable-jest][]
安装
```bash
npm i -D babel-jest
```


`.babelrc`
参考: [JavaScript compiler: Babel][]
```
{
  "env": {
    "test": {
      "presets": [
        [
          "@babel/preset-env",
          {
            "targets": {
              "node": "current"
            },
            "modules": "auto",
            "useBuiltIns": "usage",
            "corejs": {
              "version": 3,
              "proposals": true
            }
          }
        ]
      ]
    }
}
```

`package.json`
```json
{
  "scripts": {
    "test": "cross-env BABEL_ENV=test jest",
  }
}
```
