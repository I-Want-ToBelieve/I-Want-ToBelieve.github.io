---
title: prettier stylelint husky lint-staged 与 create-react-app typescript 样板集成
date: 2020-01-19 09:01:40
tags:
  - prettier
  - stylelint
  - husky
  - lint-staged
  - create-react-app
  - typescript
  - eslint
---

[prettier docs: prettier vs. linters]: https://prettier.io/docs/en/comparison.html
[prettier docs: why prettier?]: https://prettier.io/docs/en/why-prettier.html
[stylelint: why and how to lint css]: http://slides.com/ai/stylelint#/
[prettier docs: integrating-with-linters]: https://prettier.io/docs/en/integrating-with-linters.html
[stylelint docs: extend-a-shared-configuration]: https://stylelint.io/#extend-a-shared-configuration
[代码规范与项目结构]: https://floatsyi.com/2019/09/26/%E4%BB%A3%E7%A0%81%E8%A7%84%E8%8C%83%E4%B8%8E%E9%A1%B9%E7%9B%AE%E7%BB%93%E6%9E%84/
[create-react-app docs: creating-a-typescript-app]: https://create-react-app.dev/docs/getting-started#creating-a-typescript-app
[create-react-app]: https://github.com/facebook/create-react-app
[prettier]: https://github.com/prettier/prettier
[lint-staged]: https://github.com/okonet/lint-staged
[husky]: https://github.com/typicode/husky
[stylelint]: https://github.com/stylelint/stylelint
[stylelint-config-prettier]: https://github.com/prettier/stylelint-config-prettier
[stylelint-config-recommended]: https://github.com/stylelint/stylelint-config-recommended
[stylelint-prettier]: https://github.com/hugomrdias/prettier-stylelint
[eslint-config-prettier]: https://github.com/prettier/eslint-config-prettier
[eslint-plugin-prettier]: https://github.com/prettier/eslint-plugin-prettier
[vscode-eslint]: https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint
[vscode-stylelint]: https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint
[vscode-prettier]: https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode
[eslint]: https://github.com/eslint/eslint

## 参考

- [Prettier docs: Prettier vs. Linters][]
- [Prettier docs: Why Prettier?][]
- [Stylelint: Why and How to Lint CSS][]
- [Prettier docs: integrating-with-linters][]
- [stylelint docs: extend-a-shared-configuration][]
- [代码规范与项目结构][]
- [create-react-app docs: creating-a-typescript-app][]

## 资源

- [create-react-app][]
- [eslint][]
- [prettier][]
- [lint-staged][]
- [husky][]
- [stylelint][]
- [stylelint-config-prettier][]
- [stylelint-config-recommended][]
- [stylelint-prettier][]
- [eslint-config-prettier][]
- [eslint-plugin-prettier][]
- [vscode-eslint][]
- [vscode-stylelint][]
- [vscode-prettier][]

## QA

- 为什么要在已有 [eslint][] 的 [create-react-app][] 中加入 [prettier][] ?
  请参考: [Prettier docs: Prettier vs. Linters][]
  请参考: [Prettier docs: Why Prettier?][]

- 为什么要使用 [stylelint] ?
  请参考: [Stylelint: Why and How to Lint CSS][]

## 集成步骤

请参考: [Prettier docs: integrating-with-linters][]
请参考: [stylelint docs: extend-a-shared-configuration][]
请参考: [create-react-app docs: creating-a-typescript-app][]
请参考: [代码规范与项目结构][]

使用 [create-react-app][] 创建样板文件

```powershell
yarn create react-app myapp --typescript
```

添加开发时依赖

- [prettier][] [lint-staged][] [husky][]
- [stylelint][] [stylelint-config-prettier][] [stylelint-config-recommended][] [stylelint-prettier][]
- [eslint-config-prettier][] [eslint-plugin-prettier][]

```powershell
yarn add prettier lint-staged husky stylelint stylelint-prettier stylelint-config-prettier stylelint-config-recommended eslint-config-prettier eslint-plugin-prettier -D
```

添加配置文件

```
touch .eslintrc .eslintignore .gitattributes .prettierrc .stylelintrc
```

.eslintrc

```json
{
  "extends": ["react-app", "plugin:prettier/recommended"],
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```

.eslintignore

```
# build
build/
```

.gitattributes

```
* text=auto eol=lf
```

.prettierrc

```json
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": false,
  "singleQuote": true,
  "endOfLine": "lf"
}
```

.stylelintrc

```json
{
  "extends": ["stylelint-config-recommended", "stylelint-prettier/recommended"],
  "plugins": ["stylelint-prettier"],
  "rules": {
    "prettier/prettier": true
  }
}
```

package.json 删除 eslintConfig 字段并添加以下字段

```json
{
  "scripts": {
    "lint": "eslint \"src/**/*.{js,jsx,ts,tsx}\"",
    "lint:fix": "yarn lint --fix",
    "stylelint": "stylelint \"src/**/*.{css,scss}\"",
    "stylelint:fix": "yarn stylelint --fix"
  },
  "lint-staged": {
    "src/**/*.{js,jsx,ts,tsx,json,css,scss,md}": ["prettier --write", "git add"]
  },
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  }
}
```

## 命令

检查脚本

```
yarn lint
```

检查并修复脚本

```
yarn lint:fix
```

检查样式

```
yarn stylelint
```

检查并修复样式

```
yarn stylelint:fix
```

## eslint 与 stylelint 的 vscode 扩展

- [vscode-eslint][]
- [vscode-stylelint][]
- [vscode-prettier][]

vscode setting.json

```json
{
  /*
   * 插件名： ESLint插件的配置
   * 描述：根据定义的规则对相应的语言的语法风格进行严格的约束，以统一编码风格降低阅读沟通成本
   * 详情：https: //marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint
   */
  "eslint.enable": true,
  // 禁用 vscode 默认的 js 格式化
  "javascript.validate.enable": false,
  "editor.formatOnPaste": false,
  "editor.formatOnSave": false,
  // 保存时自动执行 eslint fix
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.fixAll.stylelint": true
  },
  /**
   * 插件名: stylelint
   * 描述： css 语法效验
   * 详情： https: //marketplace.visualstudio.com/items?itemName=shinnn.stylelint
   */
  "stylelint.enable": true,
  "css.validate": false,
  "less.validate": false,
  "scss.validate": false,
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  /*
   * 插件名：prettier
   * 描述：按照设定的规则格式化对应的文档
   * 详情：https: //marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode
   * 注意：此插件被 Vetur 插件依赖
   */
  "prettier.trailingComma": "es5",
  "prettier.tabWidth": 2,
  // 使用单引号？
  "prettier.singleQuote": true,
  // 要分号？
  "prettier.semi": false,
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": false
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": false
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": false
  },
  "[jsx]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": false
  },
  "[tsx]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": false
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[md]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": false
  }
}
```

-
