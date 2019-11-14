---
title: 'JavaScript compiler: Babel'
date: 2019-11-13 16:42:58
tags:
- Babel
---

[babel]: https://github.com/babel/babel
[core-js]: https://github.com/zloirock/core-js
[cross-env]: https://github.com/kentcdodds/cross-env

## 资源

- [babel][]
- [core-js][]
- [cross-env][]

## .babelrc

- [babel config file options](https://babeljs.io/docs/en/options)

## [babel][]
安装
```bash
npm i -D @babel/core @babel/preset-env @babel/cli
```

`.babelrc`
```json
{
  "env": {
    "production": {
      "presets": [
        [
          "@babel/preset-env",
          {
            "modules": false
          }
        ]
      ]
    }
  },
  "ignore": [
    "node_modules/**"
  ]
}
```

安装 [cross-env][]
```bash
npm i -D cross-env
```

`package.json`
```json
{
  "scripts": {
    "build": "rollup --config",
    "build:prod": "cross-env BABEL_ENV=production npm run build"
  }
}
```


## Polyfill: [core-js][]

安装
```bash
npm i -D core-js@3
```

`.babelrc`
```json
{
  "env": {
    "production": {
      "presets": [
        [
          "@babel/preset-env",
          {
            "modules": false,
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
}
```

## [babel-jest](https://github.com/facebook/jest#using-babel)

- [bable-jest](https://floatsyi.com/2019/11/14/bable-jest/)



