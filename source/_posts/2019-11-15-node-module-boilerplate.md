---
title: node-module-boilerplate
date: 2019-11-15 22:14:14
tags:
- npm
- node-module
- boilerplate
---

> 愚蠢的人让神经网络像机器的硬盘一样记忆信息, 聪明的人让机器模仿学习像人类一样深邃的思考.

[代码规范与项目结构]: https://floatsyi.com/2019/09/26/%E4%BB%A3%E7%A0%81%E8%A7%84%E8%8C%83%E4%B8%8E%E9%A1%B9%E7%9B%AE%E7%BB%93%E6%9E%84/
[前端构建工具]: https://floatsyi.com/2019/10/06/%E5%89%8D%E7%AB%AF%E6%9E%84%E5%BB%BA%E5%B7%A5%E5%85%B7/
[持续集成]: https://floatsyi.com/2019/11/09/%E6%8C%81%E7%BB%AD%E9%9B%86%E6%88%90/
[JavaScript compiler: Babel]: https://floatsyi.com/2019/11/13/JavaScript-compiler-Babel/
[JavaScript Testing Framework: jest]: https://floatsyi.com/2019/11/13/JavaScript-Testing-Framework-jest/
[bable-jest]: https://floatsyi.com/2019/11/14/bable-jest/

[eslint-config-standard]: https://github.com/standard/eslint-config-standard
[eslint]: https://github.com/eslint/eslint
[rollup]: https://www.rollupjs.org/guide/en/
[rollup/awesome]: https://github.com/rollup/awesome
[lint-staged]: https://github.com/okonet/lint-staged
[husky]: https://github.com/typicode/husky
[chalk]: https://github.com/chalk/chalk
[github]: https://github.com/
[jest]: https://github.com/facebook/jest

[node-module-boilerplate]: https://github.com/FloatingShuYin/node-module-boilerplate

## 参考
- [代码规范与项目结构][]
- [前端构建工具][]
- [持续集成][]
- [JavaScript compiler: Babel][]
- [JavaScript Testing Framework: jest][]
- [bable-jest][]

## 资源
- [eslint-config-standard][]
- [eslint][]
- [rollup][]
- [rollup/awesome][]
- [lint-staged][]
- [husky][]
- [jest][]

## [node-module-boilerplate][]

### 使用 npm 初始化项目
```bash
cd x:/git.workspace/node-module-boilerplate
npm init --scope=floatsyi
```

### 使用 [rollup][] 构建工具, 构建现代化 node package

1. 使用 npm 添加开发时依赖: rollup
```bash
npm i rollup -D
```

2. 创建基本的目录结构
```bash
mkdir -p src/index.js __test__/ build coverage rollup.config.js
```

3. 添加以下内容到 `rollup.config.js`
参考: [前端构建工具][]
```js
import babel from 'rollup-plugin-babel'
import { terser } from 'rollup-plugin-terser'
import commonjs from 'rollup-plugin-commonjs'
import resolve from 'rollup-plugin-node-resolve'
import filesize from 'rollup-plugin-filesize'

export default {
  input: 'src/index.js',
  output: [
    {
      file: 'build/index.cjs.js',
      format: 'cjs'
    },
    {
      file: 'build/index.esm.js',
      format: 'es'
    }
  ],
  external: ['core-js'],
  plugins: [
    resolve(),
    babel(),
    commonjs(),
    terser({
      output: {
        // 保留版权注释
        comments (node, comment) {
          const text = comment.value
          const type = comment.type
          if (type === 'comment2' /* multiline comment */) {
            return /preserve|license|cc_on/i.test(text)
          }
        }
      }
    }),
    filesize()
  ]
}
```

4. 添加以下 npm script
package.json:
```json
{
  "main": "build/index.cjs.js",
  "module": "build/index.esm.js",
  "files": [
    "build"
  ],
  "script": {
     "build": "rollup --config"
  }
}
```

### 使用 [jest][] 测试框架测试代码
参考: [JavaScript Testing Framework: jest][]

### 使用 [eslint][] 和 [eslint-config-standard][]
参考: [代码规范与项目结构][]
1. 使用 npm 添加开发时依赖性: [eslint][] 和 [eslint-config-standard][]
```bash
npm i -D eslint
npm install --save-dev eslint-config-standard eslint-plugin-standard eslint-plugin-promise eslint-plugin-import eslint-plugin-node
```

2. 新建 `.eslintrc` 和 `.eslintignore` 文件
```bash
touch .eslintrc .eslintignore
```
  `.eslintrc`:
  ```json
  {
    "extends": "standard"
  }
  ```
  `.eslintignore`:
  ```
  build/**
  ```

3. 添加以下 npm script
package.json:
```json
{
  "script": {
    "lint": "eslint .",
    "lint:fix": "eslint --fix ."
  }
}
```

### 使用 [lint-staged][] , [husky][] 以及 [commitlint][] 规范 git staged files 和 git commit message
1. 使用 npm 添加开发时依赖: lint-staged \ husky \ commitlint
```bash
npm i -D husky lint-staged
npm install --save-dev @commitlint/config-angular @commitlint/cli
npm install --save-dev @commitlint/prompt @commitlint/prompt-cli
```

2. 添加以下内容到 `package.json`
package.json
```json
{
  "scripts": {
    "commit": "commit"
  },
  "lint-staged": {
    "*.js": [
      "eslint --fix",
      "git add"
    ]
  }
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged",
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
}
```

3. 添加以下内容到 `commitlint.config.js`
commitlint.config.js:
```js
module.exports = { extends: ['@commitlint/config-angular'] }
```

### 使用 [semantic-release][] 语义化版本号
1. 使用 npm 将 semantic-release-cli 安装至全局
```bash
npm install -g semantic-release-cli
```

2. 执行 `semantic-release-cli setup`
```bash
semantic-release-cli setup
```
![semantic-release-cli setup](https://github.com/semantic-release/semantic-release/blob/master/media/semantic-release-cli.png)

### [codecov][]
1. 使用 npm 添加开发时依赖: codecov
```bash
npm install codecov --save-dev
```

2. 添加以下 npm script
package.json:
```json
{
  "script": {
    "codecov": "codecov"
  }
}
```

### 新建一个 github 仓库, 对代码进行版本管理
1. 登录 [github][] 并新建一个名为 `node-module-boilerplate` 的仓库

2. 使用 git 命令行工具将本地工作目录链接到 github 服务器的仓库
```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:FloatingShuYin/node-module-boilerplate.git
git pull --set-upstream origin master
git push
```
3. 使用编辑器打开工作目录并重装 husky
```bash
code .
npm uninstall husky
npm install -D husky
npm audit fix
```


