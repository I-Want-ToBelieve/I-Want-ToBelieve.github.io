---
title: 'JavaScript Testing Framework: jest'
date: 2019-11-13 14:30:00
tags:
- 测试
- jest
---

[jest]: https://github.com/facebook/jest

## 资源

- [jest][]

## [jest.config.js](https://jestjs.io/docs/zh-Hans/configuration)

- [Configuring Jest](https://jestjs.io/docs/zh-Hans/configuration)

## [jest][]
安装 jest
```bash
npm install --save-dev jest
```

jest.config.js
```js
// For a detailed explanation regarding each configuration property, visit:
// https://jestjs.io/docs/en/configuration.html

module.exports = {
  collectCoverage: true,
  testEnvironment: 'node',
  testMatch: ['<rootDir>/__tests__/**/*spec.js']
}
```

`package.json`
```json
{
  "scripts": {
    "test": "jest",
  },
}
```


## [babel-jest](https://github.com/facebook/jest#using-babel)

- [bable-jest](https://floatsyi.com/2019/11/14/bable-jest/)






