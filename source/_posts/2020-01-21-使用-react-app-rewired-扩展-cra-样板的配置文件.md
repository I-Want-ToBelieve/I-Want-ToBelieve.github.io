---
title: 使用 react-app-rewired 扩展 cra 样板的配置文件
date: 2020-01-21 10:07:01
tags:
- react-app-rewired
- cra
---

[react-app-rewired]: https://github.com/timarney/react-app-rewired
[tailwindcss]: https://github.com/tailwindcss/tailwindcss
[prettier stylelint husky lint-staged 与 create-react-app typescript 样板集成]: https://floatsyi.com/2020/01/19/prettier-stylelint-husky-lint-staged-%E4%B8%8E-create-react-app-typescript-%E6%A0%B7%E6%9D%BF%E9%9B%86%E6%88%90/

## 参考
- [prettier stylelint husky lint-staged 与 create-react-app typescript 样板集成][]

## 资源
- [react-app-rewired][]
- [tailwindcss][]

## 安装 [react-app-rewired][]
添加开发时依赖
```
yarn add react-app-rewired -D
```

新建 config-overrides.js
```
touch config-overrides.js
```

config-overrides.js
```js
module.exports = function override(config, env) {
  //do stuff with the webpack config...
  return config
}
```

package.json
```json
  "scripts": {
-   "start": "react-scripts start",
+   "start": "react-app-rewired start",
-   "build": "react-scripts build",
+   "build": "react-app-rewired build",
-   "test": "react-scripts test --env=jsdom",
+   "test": "react-app-rewired test --env=jsdom",
    "eject": "react-scripts eject"
}
```

## 配置 [stylelint](https://github.com/stylelint/stylelint) 和 [tailwindcss][]
添加开发时依赖
```
yarn add stylelint-webpack-plugin -D
```
运行时依赖
```
yarn add tailwindcss
```

config-overrides.js
```js
const StylelintPlugin = require('stylelint-webpack-plugin')
const postcss = require('react-app-rewire-postcss')
// https://tailwindcss.com/docs/controlling-file-size/
const purgecss = require('@fullhuman/postcss-purgecss')({
  // Specify the paths to all of the template files in your project
  content: [
    './src/**/*.tsx',
    // etc.
  ],

  // Include any special characters you're using in this regular expression
  defaultExtractor: content => content.match(/[\w-/:]+(?<!:)/g) || [],
})
// https://github.com/timarney/react-app-rewired
module.exports = {
  webpack: function(config, env) {
    const isDev = env === 'development'
    const isPro = env === 'production'

    // https://github.com/csstools/react-app-rewire-postcss
    postcss(config, {
      ident: 'postcss',
      plugins: [
        require('tailwindcss'),
        require('autoprefixer'),
        ...(isPro ? [purgecss] : []),
      ],
    })

    if (isDev) {
      // https://vanja.gavric.org/blog/integrate-stylelint-into-create-react-app-without-ejecting/
      // https://github.com/webpack-contrib/stylelint-webpack-plugin
      config.plugins.push(
        new StylelintPlugin({
          // options here
        })
      )
    }

    return config
  },
}
```

tailwind.config.js
```js
// https://tailwindcss.com/docs/configuration
module.exports = {
  important: false,
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [],
}
```

