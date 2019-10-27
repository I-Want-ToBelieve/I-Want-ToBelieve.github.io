---
title: 使用 shadow DOM 隔离宿主的样式作用域
date: 2019-10-19 12:56:12
tags:
- shadow DOM
---
![Syntax highlighting codepen prototype screenshot](http://r.photo.store.qq.com/psb?/V12iDrZG1mzmnh/CpGYADfWtj75eVpaAVZx8OODaycDD7ynd2xOJEPUpwE!/r/dL4AAAAAAAAA)

[tampermonkey script: Syntax highlighting]: https://greasyfork.org/zh-CN/scripts/391243-syntax-highlighting
[Element.attachShadow()]: https://developer.mozilla.org/en-US/docs/Web/API/Element/attachShadow
[Syntax highlighting codepen prototype]: https://codepen.io/FloatingShuYin/pen/GRRjmOE?editors=0010
[highlight.js]: https://highlightjs.org/
[google fonts]: https://fonts.google.com/
[tampermonkey documentation]: https://www.tampermonkey.net/documentation.php
[buefy]: https://buefy.org/
[fontface Observer]: https://github.com/bramstein/fontfaceobserver

## 资源
- [Element.attachShadow()][]
- [tampermonkey documentation][]
- [tampermonkey script: Syntax highlighting][]
- [Syntax highlighting codepen prototype][]
- [highlight.js][]
- [google fonts][]
- [fontface Observer][]
- [buefy][]

## [tampermonkey script: Syntax highlighting][]

花了 ~~将近两天时间~~ 几天时间, 边构思, 边实践, 实现了一个使用 highlight.js 高亮页面中的代码片段的油猴脚本.
一开始的逻辑十分简单, 直接遍历页面中的 `pre code` 节点, 然后使用 highlight.js 高亮即可.
后来又不仅想高亮, 还想要换字体, 换主题, 随需求增长所带来的复杂度已经足够写一个 UI 界面来配置这些选项.
于是问题就来了,  该如何使得 UI 界面注入到宿主页面中并不受宿主页面的影响?

## shadow DOM

早就听闻 shadow DOM 各种神奇, 一试之下果然非常给力.
shadow DOM 最引人注目的特性是可以隔离宿主样式作用域, 另辟天地.
正得益于此, 我们只需要创建 HTML 和 Body 元素挂载到 Shadow DOM 上,
我们的页面就像是在新的页面上打开的一样.

节选一段 Syntax highlighting 相关源码
```js
// 设置页
let parasitifer = null
const openSetting = () => {
  // 非首次调用
  if (parasitifer) {
    parasitifer.show()
    return true
  }

  parasitifer = document.createElement('div') // 此 DOM 节点将用作 shadowDOM 的载体被插入宿主的 DOM 节点中.
  parasitifer.id = 'host-element'
  parasitifer.style = `position: fixed;top:0;bottom:0;z-index:9999;width:100vw;height:100vh;font-size:16px;background-color:#fff;`
  parasitifer.show = () => {
    parasitifer.style.display = 'block'
  }
  parasitifer.hide = () => {
    parasitifer.style.display = 'none'
  }

  const shadowRoot = parasitifer.attachShadow({ mode: 'open' })
  // 此节点将成为 shadowDOM 的直接子元素, 包裹一切, 所以用 HTML 元素很合适.
  // 不仅仅是语义上的合适, 大多数的 UI 库都需要一个结构完整的 DOM 树用来做自适应布局.
  const shadowContent = document.createElement('HTML')
  const shadowStyleEle = document.createElement('style')
  const bulmaStyleEle = document.createElement('style')
  const fontStyleEle = document.createElement('style')
  const themeStyleEle = document.createElement('style')
  const vueContainer = document.createElement('div') // 这个 DOM 节点不会显示在 DOM 树中, 而是作为 vue 的挂载点,同来渲染 vue 的模板.
  vueContainer.id = 'vue-root'
  // shadow DOM 的样式作用域隔离是非常实用的特性, 完全不受宿主环境影响的样式, 轻盈的开始
  shadowStyleEle.innerText = ``
  shadowContent.appendChild(shadowStyleEle)
  shadowContent.appendChild(bulmaStyleEle)
  shadowContent.appendChild(fontStyleEle)
  shadowContent.appendChild(themeStyleEle)
  shadowContent.appendChild(vueContainer)
  shadowRoot.appendChild(shadowContent)
  document.body.appendChild(parasitifer)

  const mount = style => {
    bulmaStyleEle.innerText = style

    const vueRoot = document
      .querySelector('#host-element')
      .shadowRoot.querySelector('#vue-root')
    // 这里使用 body 元素 作为父节点, 结合上面创造的 HTML 元素是为了给 UI 组件一个完整的上下文环境, 就像在一个新的 HTML 页面中一样.
    const vueTemplate =
      `<body style="height: 100vh">
        <div id="app-vue" class="container">
          Other DOM
        </div>
      </body>`
    const vm = new window.Vue({
      el: vueRoot,
      template: vueTemplate,
      data () {
        return {
          // some data
        }
      },
      watch: {
        // watch something
      },
      methods: {
        // some methods
      },
      mounted () {
        // init something
      }
    })
}
```
其中值得特别注意是 `vue` 的 `el` 选项.
