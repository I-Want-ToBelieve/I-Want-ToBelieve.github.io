---
title: python --> javascript 全栈指南
date: 2019-06-14 13:50:31
tags:
- python
- python 至 JS
categories:
- 文档
- python 至 JS
---

你需要[科学上网](https://github.com/shadowsocks/shadowsocks-windows)才能加载评论组件

## 参考

- [developer-roadmap ------ @github](https://github.com/kamranahmedse/developer-roadmap)
- [简明python ------ @gitbook](https://bop.mol.uno/04.about_python.html)

## 资源
- [JavaScript 资源大全中文版，内容包括：包管理器、加载器、测试框架、运行器、QA、MVC框架和库、模板引擎等](https://github.com/jobbole/awesome-javascript-cn)

---------

## 计算机是如何计算的,编译器是如何编译的


> 从下而上的从想象中构建电子世界,
仰望前辈们欣勤建立的计算机大厦,
你会得到从上而下洞悉黑色盒子的能力,
你无法也不必关注太多的细节,
俯视电子世界,所有的电子河流都要回到电子海洋.


[极简编译器原理 ------ @bilibili 时长: 1小时](https://www.bilibili.com/video/av51948975)

python 被 python 的解释器 Cpython(官方默认的解释器) 或者 PyPy(支持JIT) 转换成字节码
然后再由字节码虚拟机把字节码转换成机器语言

**python 人类可读的源代码 --> 字节码 --> 机器可读的机器语言**

JS 也是如此,
JS 被 JS 的解释器 v8(chrome浏览器和node的解释器,支持JIT) 转换成字节码
然后再由字节码虚拟机把字节码转换成机器语言

**javascript 人类可读的源代码 --> 字节码 --> 机器可读的机器语言**

### JS 与 node 与 python 语法比对

> 毫无疑问, 这是比对学习法的最佳应用场景.

在比对之前, 必须说明下, 什么是ES5, ES6.

JS 这门语言一直在持续更新, ECMAScript 是 JS 的语法标准,
你可以简单的理解为, ES5 是 python 2.x, ES6 是 python 3.x
现在普遍被浏览器所支持的版本是 ES5, 而 ES6 也已经被大多数现代浏览器所支持,
对于不支持 ES6 语法的浏览器, 我们可以通过 [babel](https://babeljs.io/) 将其编译为 ES5,
而新添加的 API 则可以通过添加 [polyfill](https://developer.mozilla.org/zh-CN/docs/Glossary/Polyfill) 以兼容老旧的浏览器.

以下内容如果是 ES6 甚至是 ES7 版本的, 我会将其标注出来.

#### Hello World

python:

```python
print('Hello World')
```

JS 与 node:

```js
console.log('Hello World')
```

#### 注释

python:

```python
# 单行注释

'''
多行
注释
'''
```

JS 与 node:

```js
// 单行注释

/* 多行
 * 注释
*/
```

#### 变量

python:

```python
# 局部变量
value = 0

# 全局变量
global str = 'i\'m global string'
```

JS 与 node:

```js
// 局部变量
var value = 0

let value_0 = 1 // ES6

// 不可二次赋值的常量
const VALUE = 1 // ES6

// ES6 新增的解构赋值
const a = 0
const b = 1
const c = 2
// 简写为:
const [a, b, c] = [0, 1, 2]


// 全局变量
window.str = 'i\'m global string in brower' // 在浏览器中

global.str = 'i\'m global string in node'// 在 node 中

```

#### 字符串

python:

```python
# 单行字符串
'我是字符串'

# 多行字符串
'''
我是多行
字符串
'''
```

JS 与 node:

```js
// 单行字符串

'我是字符串'

// 多行字符串 (ES6, 这个符号通过 shift + ~打出)

`我是多行
字符串`
```

#### 格式化方法(模板字符串)

python:

```python
str = 'World'

print('Hello {}'.format(str)) # 'Hello World'
```

JS 与 node:

```js
const str = 'World'

console.log(`Hello ${str}`) // 'Hello World' (ES6)
```

#### 运算符与表达式

```python
# 等于
==

# 不等
!=

# 或
or

# 与
and

# 非
not

# 整除
//
```

JS 与 node:

```js
// 等于
===

// 不等
!==

// 或
||

// 与
&&

// 非
!

// 没有整除符号

// 自增 自减
let n = 0 // ES6

n++ // 是 n = n + 1 的简写

console.log(n) // 1
```

#### 控制流

##### `if` 语句

python:

```python
a = 0
b = 1
c = 2

if a > b:
    print('a > b')
elif a > c:
    print('a > c')
else:
    print('a < b and a < c')

# 单条 if

if Ture:
    print('true')
```

JS 与 node:

```js
const [a, b, c] = [0, 1, 2]


if (a > b) {
  console.log('a > b')
} else if (a > c){
  console.log('a > c')
} else {
  console.log('a < b and a < c')
}

// 单条 if 可省略花括号

if (true) console.log('true')

```

##### `while` 语句

python:

```python
a = 0
b = 10

while a < b:
    a += 1
    print('第 {} 次循环'.format(a))
```

JS 与 node:

```js
let a = 0 // ES6
const b = 10 // ES6

while (a < b) {
  a += 1
  console.log(第 ${a} 次循环)
}

```

##### `for` 循环

python:

```python

arr = [0, 1, 2, 3]

for i in arr:
    print(i)
```

JS 与 node:

```js
const arr = [0, 1, 2, 3] // ES6

for (const i of arr) { // ES6
  console.log(i)
}
```
##### 函数

python:

```python
def say_hello():
    print('hello world')
```

JS 与 node:

```js
// js 有三种写法...

function say_hello() {
  console.log('hello world')
}

var sayHello = function () {
  console.log('hello world')
}

const say_hello = () => { // ES6 匿名箭头函数
  console.log('hello world')
}

```

##### 可变参数

python:

```python
def total(a=5, *numbers, **phonebook):
    print('a', a)

    # 遍历元组中的所有项目
    for single_item in numbers:
        print('single_item', single_item)

    # 遍历字典中的所有项目
    for first_part, second_part in phonebook.items():
        print(first_part,second_part)

print(total(10,1,2,3,Jack=1123,John=2231,Inge=1560))

# 输出
# a 10
# single_item 1
# single_item 2
# single_item 3
# Inge 1560
# John 2231
# Jack 1123
# None
```

JS 与 node:

```js
const total = (a = 5, phonebook, ...numbers) => { // ES6
  // ...numbers 是一个列表(数组),存储了所有剩余的参数: [1, 2, 3]
  console.log('a', a)
  // js 中没有元组 只有列表(数组)
  for (const single_item of numbers) {
    console.log('single_item', single_item)
  }
  // 遍历字典(对象)中的所有项目
  for ( const [first_part, second_part] of Object.entries(phonebook)) { // ES6 的解构赋值
    console.log(first_part,second_part)
  }
}

console.log(total(10, {Jack: 1123,John: 2231, Inge: 1560}, 1, 2, 3))

// 输出
// a 10
// VM331:6 single_item 1
// VM331:6 single_item 2
// VM331:6 single_item 3
// VM331:10 Jack 1123
// VM331:10 John 2231
// VM331:10 Inge 1560
// VM331:14 undefined

```
##### 模块

python:

```python
import sys
from math import sqrt

print('\n\nThe PYTHONPATH is', sys.path, '\n')
print("Square root of 16 is", sqrt(16))

```

JS 与 node:

```js
// ES5 没有模块功能...

// ES6

import lodash from 'lodash'
import { clone } from 'lodash'

const obj = lodash.clone({})
const obj_1 = clone({})

// node
const os = required('os')
const release = required('os').release

```

##### 类

python:

```python
class Person:
    def __init__(self, name):
        self.name = name

    def say_hi(self):
        print('Hello, my name is', self.name)

p = Person('Swaroop')
p.say_hi() # Hello, my name is Swaroop

```

JS 与 node:

```js
// ES5 没有类...

// ES6

class Person {
  constructor (name) {
    this.name = name
  }

  say_hi () {
    console.log('Hello, my name is', this.name)
  }
}
const p = new Person('Swaroop')
p.say_hi() // Hello, my name is Swaroop
```

##### 深入理解

以下两本通读一遍, 不要死记, 理解最重要

[JavaScript 标准参考教程（alpha）(ES5语法: 1-5章节)](http://javascript.ruanyifeng.com/#toc0)
[ECMAScript 6 入门](http://es6.ruanyifeng.com/#README)

-----------------------

## 开发环境搭建

- [development-environment-manual ------ @github 时长: 10分钟](https://github.com/FloatingShuYin/development-environment-manual)
- [javascript 开发环境搭建(windows 10) ------ @github 时长: 10分钟](https://github.com/FloatingShuYin/development-environment-manual/blob/master/javascript.md)
- [python 开发环境搭建(windows 10) ------ @github 时长: 10分钟](https://github.com/FloatingShuYin/development-environment-manual/blob/master/python.md)

-------------------------

## JS 与 node 以及 python 的运行环境


> 上帝说: "要有光!",于是,就有了光.

### Node.JS 的结构

[Node.JS 架构概览 ------ @segmentfault 时长: 15分钟](https://segmentfault.com/a/1190000005892501)

JS 大多都运行在浏览器中,
而 node 就是 使用 JS 语法 的 python ,
node 和 python 都可以进行高权限的 io 操作, 因此可以在服务器上工作.

node 需要运行 JS 于是它集成了 v8 ,
node 需要异步 io 于是它集成了 libuv.
如此等等...

v8 和 libuv 这些都是什么? 它们都是一个个黑色的盒子,
你只需要在\需要了解它的时候\了解它.

 ### 浏览器的结构

[史上最全！图解浏览器的工作原理 ------ @infoq 时长: 20分钟](https://www.infoq.cn/article/CS9-WZQlNR5h05HHDo1b)

[浏览器内核、JS 引擎、页面呈现原理及其优化 ------ @zybuluo 时长: 25分钟](https://www.zybuluo.com/yangfch3/note/671516)

chrome 浏览器需要渲染页面于是就集成了 webKit,
chrome 浏览器需要解析 XML 于是就集成了 libXML,
chrome 浏览器需要运行 JS 于是就集成了 v8.

如此等等...

没有太多的理由, 就像大地需要树, 于是大地就生长出了树.
树, 是一种优美的植物, 在电子世界里, 树, 是一种优美的数据结构.
它的层次之美,让它承载着茂盛的树冠.

这样华美的页面大概也只有树才能够支撑的起吧.

### 浏览器中的树: HTML + CSS + JS

[HTML5 and CSS,边写边练,所见即所得,快速入门 ----- @FreeCodeCamp 时长: 5小时](https://www.freecodecamp.cn/challenges/say-hello-to-html-element)
[初识HTML+CSS ------ @幕客网 时长: 9小时](https://www.imooc.com/learn/9)

> 与生俱来的遗忘机制使我们没办法记住所有的细节,
而值得庆幸的是软件开发并不是一场愚蠢的闭卷考试.

- [HTML标签速查文档](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)
- [HTML标签速查文档-分类版](https://www.w3cschool.cn/html/dict)
- [CSS速查文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)
- [CSS速查文档-分类版](https://www.w3cschool.cn/css/dict)


>人们需要网页排版合理,有结构,于是就有了HTML.
人们需要网页华美绚丽,有色彩,于是就有了CSS.
人们需要网页动态活泼,有逻辑,于是就有了JS.

HTML是一种 类XML数据结构, 它是树,它是浏览器中的树.

它最开始是这样的:

```html
<html>
  <head>
    <title>Hello World</title>
    <style></style>
    <script></script>
  </head>
  <body>
  </body>
</html>
```

它最后会成为你心中的样子,
HTML是树,
是你心中的树.

-------------------------------------

#### css 眼中的树

css眼中的树是方方正正的.

> CSS 装饰着 HTML 这株树, 成为了树的一部分.

##### 选择器

css 总想改变树的样子,
它需要选择树的某一部分,
选择它,然后改变它.

[选择器全列表](https://www.w3cschool.cn/css/dict)

[前端杂谈: CSS 权重 (Specificity) @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/50322177)


##### 盒子模型

[盒子模型 ------ @知乎 时长: 10分钟](https://zhuanlan.zhihu.com/p/59612287)

建议使用 IE 盒子模型:

```css
* {
  box-sizing: border-box;
}
```

##### 块级格式化上下文(Block Formatting Context)

我想你会喜欢这样的方块.

[学习 BFC (Block Formatting Context) ------ @掘金 时长: 20分钟](https://juejin.im/post/59b73d5bf265da064618731d)

[css_11 | CSS——让“盒子”动起来：② “定位”和 BFC  @知乎 时长: 20分钟](https://zhuanlan.zhihu.com/p/64366441)

##### 布局

[学习 CSS 布局 ------ @learnlayout 时长: 20分钟](http://zh.learnlayout.com/)

###### flex 容器

[Flex ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/46684565)

###### grid 容器

[轻松快速学习 Grid 布局 ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/46754464)

[最全～ Grid vs Flex ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/46757975)

[一行css代码搞定响应式布局 ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/69809343)

##### 重置默认样式

由于各个浏览器会存在各不相同的默认 css 样式,
我们需要引入一个第三方库来让这些默认样式保持统一.

[Normalize.css](https://necolas.github.io/normalize.css/)
[在 Normalize.css 基础上更进一步 ------@zhihu 时长: 5分钟](https://zhuanlan.zhihu.com/p/60816003)

##### 垂直居中

[16种方法实现水平居中垂直居中 ------ @掘金 时长: 15分钟](https://juejin.im/post/58f818bbb123db006233ab2a)
[CSS 实现水平垂直居中的1010种方式（史上最全）------ @掘金 时长: 15分钟](https://juejin.im/post/5b9a4477f265da0ad82bf921)

不考虑兼容性的话,
使用flex的方案最好,
这是标准方案.

##### 清除浮动

[CSS中的浮动和清除浮动 ------ @简书 时长: 10分钟](https://www.jianshu.com/p/09bd5873bed4)


##### px、em、rem、%、vw、vh、vm

[px、em、rem、%、vw、vh、vm这些单位的区别 ------ @知乎 时长: 5分钟](https://zhuanlan.zhihu.com/p/66686493)

##### CSS隐藏元素的几种方式及区别

[从隐藏元素谈起 ------ @知乎 时长: 5分钟](https://zhuanlan.zhihu.com/p/23977353)

##### 渐进增强与优雅降级

[CSS选择 “渐进增强” 还是 “优雅降级”？ ------ @知乎 时长: 5分钟](https://www.zhihu.com/question/29634882)
[需警惕CSS3属性的书写顺序](https://www.zhangxinxu.com/wordpress/2010/09/%E9%9C%80%E8%AD%A6%E6%83%95css3%E5%B1%9E%E6%80%A7%E7%9A%84%E4%B9%A6%E5%86%99%E9%A1%BA%E5%BA%8F/)

##### CSS 代码规范

> 计算机科学中只有两个难题: 缓存失效和命名 ——Phil Karlton

[CSS 命名规范](http://getbem.com/naming/)
[CSS 编码规范 ------ @github 时长: 10分钟](https://github.com/ecomfe/spec/blob/master/css-style-guide.md)

--------------------------------------

#### JS 眼中的树

JS 眼中的树是抽象的.

##### DOM (Document Object Model)

浏览器把 HTML 这株树给抽象成了 DOM,
JS 通过调用 DOM 获得了 创建与毁灭 HTML 这株树的能力.

[DOM 模型 ------ @JavaScript 标准参考教程（alpha）(第6章) 时长: 20分钟](http://javascript.ruanyifeng.com/#dom)
[DOM 脑图](http://naotu.baidu.com/file/066f228731f401d54b19d033e660310d?token=c250785699717806)

[详解 HTML attribute 和 DOM property ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/70671215)

##### CSSOM

浏览器把 HTML 树上的 CSS 给抽象成了 CSSOM,
JS 通过调用 CSSOM 获得了 修改 CSS 的能力.

[初探CSS对象模型（CSSOM）------ @w3cplus 时长: 5分钟](https://www.w3cplus.com/javascript/cssom-css-typed-om.html)

##### 浏览器里的 JS, BOM (Brower Object Model)

浏览器 把它自身 抽象成了 BOM,
JS 通过调用 BOM 获得了感知其载体------浏览器的能力.

[浏览器环境 ------ @JavaScript 标准参考教程（alpha）(第7章) 时长: 20分钟](http://javascript.ruanyifeng.com/#bom)

-------------------------------------------------

### 深入理解 JS 执行逻辑

#### 调用堆栈

[理解JavaScript 中的执行上下文和执行栈 ------ @github](https://github.com/yygmind/blog)

#### 作用域闭包

[深入浅出图解作用域链和闭包 ------ @github ](https://github.com/yygmind/blog)

#### this 关键字

[JavaScript深入之史上最全--5种this绑定全面解析 ------ @github](https://github.com/yygmind/blog)

#### 深浅拷贝原理

[详细解析赋值、浅拷贝和深拷贝的区别 ------ @github ](https://github.com/yygmind/blog)

#### 原型链与继承

继承随便看看, 用 ES6 的 extend 关键字就好

[重新认识构造函数、原型和原型链 ------ @github ](https://github.com/yygmind/blog)

#### 高阶函数

[JavaScript 高阶函数浅析 ------ @github](https://github.com/yygmind/blog)

#### 事件机制

#### 事件循环(Event Loop) 以及 宏任务与微任务

[一次弄懂Event Loop ------ @知乎 时长: 20分钟](https://zhuanlan.zhihu.com/p/55511602)

#### 回调

#### Promise

[这是一篇傻瓜都能看懂的Promises文章！------ @知乎 时长: 20分钟](https://zhuanlan.zhihu.com/p/24684803)

#### Async/Await原理

#### 安全

[前端安全系列之一：如何防止XSS攻击？ ------ 知乎 时长: 25分钟](https://zhuanlan.zhihu.com/p/45568315)
[前端安全系列之二：如何防止CSRF攻击？------ 知乎 时长: 40分钟](https://zhuanlan.zhihu.com/p/46592479)

[了解OWASP十大安全风险,以及使用 node 的解决方案](https://github.com/OWASP/NodeGoat)

#### 性能优化

[最强前端性能优化，Google已经为你准备好了 ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/67134654)

[你真的了解回流和重绘吗 ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/52076790)

### HTTP

[前端应该知道的http协议 ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/62191708)

### 跨域

### API

#### Result API

#### GraphQL API

[基于 JWT + Refresh Token 的用户认证实践 ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/52300092)

## 版本管理: Git

[如何优雅地使用 Git？------  @知乎 时长: 5分钟](https://www.zhihu.com/question/20866683/answer/705180453)
[Pro Git简体中文版](http://iissnan.com/progit/)

[如何配置 Git Commit Message ------  @知乎 时长: 10分钟](https://zhuanlan.zhihu.com/p/69635847)

## 升级的 css, 预编译语言: sass(scss)

### 移动端适配

[前端基础知识概述 -- 移动端开发的屏幕、图像、字体与布局的兼容适配 ------ @juejin 时长: 10分钟](https://juejin.im/post/5d70747cf265da03e16897c8)

让设计师根据 iphone 6 750px 的视口宽度设计 UI,


#### REM

使用以下 scss 适配代码,
此时设计图的 1px = 0.01rem.

```scss
html {
  font-size: calc(100vw/7.5); /* 当100vm = 750px时, font-size = 100px*/
  font-size: -webkit-calc(100vw/7.5);
  -webkit-text-size-adjust: 100%;

  body{
    font-size: 0.16rem; /* 1rem = 100px */
  }
}
```

#### VM

使用 postcss 插件: postcss-px-to-viewport
```js
// .postcssrc.js

module.exports = {
  "plugins": {
      // ...
    "postcss-px-to-viewport": {
      viewportWidth: 750, // 视口宽度，这里设置为跟设计稿宽度一致；
      viewportHeight: 1334, // 视口高度
      unitPrecision: 3, // 转换后值的精度(小数位)
      viewportUnit: 'vw', // 输出单位
      selectorBlackList: ['.usepixel'], // 黑名单
      minPixelValue: 1, // 触发转换的最小值, 大于等于这个值才会转换
      mediaQuery: false // 是否转换媒体查询中的像素
    },
    // ...
  }

}
```

## 升级的 JS: ES6,ES7...

[ES7 ES8 ES9 ES10 新特性总结思考 ------ @知乎 时长: 15分钟](https://zhuanlan.zhihu.com/p/67492465)

## 有类型的 JS: TypeScript

[TypeScript 高级技巧 ------ @掘金 时长: 20分钟](https://juejin.im/post/5cffb431f265da1b7401f466)

## 在服务器运行的 JS: Node

### node 的事件循环(Event Loop)

### node 的 pip: npm (node package manager)

### JS 代码规范

[你可能不知道的 JavaScript 代码规范 ------ 掘金 时长: 10分钟](https://juejin.im/entry/5a02d18d6fb9a045076f178e)

#### Standard

[Standard](https://github.com/standard/standard) 是现在 JS 最流行的规范, 也是能让你的代码最简洁的规范.

细则如下:

- 使用两个空格 – 进行缩进
- 字符串使用单引号 – 需要转义的地方除外
- 不再有冗余的变量 – 这是导致 大量 bug 的源头!
- 无分号 – 这没什么不好。不骗你！
- 行首不要以 `(`, `[`, or \``\` 开头, 这是省略分号时唯一会造成问题的地方
- 关键字后加空格 `if (condition) { ... }`
- 函数名后加空格 `function name (arg) { ... }`
- 坚持使用全等 `===` 摒弃 `==` 一但在需要检查 `null || undefined` 时可以使用 `obj == null`。
- 一定要处理 Node.js 中错误回调传递进来的 err 参数。
- 使用浏览器全局变量时加上 window 前缀 – document 和 navigator 除外
- 避免无意中使用到了这些命名看上去很普通的全局变量， open, length, event 还有 name。

你可以在这里查看实际的[例子](https://github.com/standard/standard/blob/master/docs/RULES-zhcn.md#javascript-standard-style)以加深理解

##### ESLints

[ESLints](https://github.com/eslint/eslint) 是一个实时代码格式检查工具, 它也可以在你保存文件修改时自动按照你定义好的 JS 代码规范来格式化你的代码.

[ESLints 中文网](http://eslint.cn/)

你可以参考下面这篇文章以及 [ESLints 官方文档](http://eslint.cn/docs/user-guide/getting-started)配置适合自己的 ESLints 配置文件:

[深入浅出 eslint ——关于我学习 eslint 的心得 ------ @掘金 时长: 5分钟](https://juejin.im/post/5bab946cf265da0ae92a75ca#heading-0)

ESLints 的配置文件一般包含在脚手架提供的项目模板中,
不需要我们自己写,
不过参考上面的文档现配一个也很简单.

如果你需要自己写 eslint 插件的话:

[开发 eslint 规则 ------ 掘金 时长: 20分钟](https://juejin.im/post/5bb079ede51d450e5d0b350a)

###### 在 ESLints 中使用 Standard 规范

[eslint-config-standard](https://github.com/standard/eslint-config-standard)

### 工程化的前端, 打包工具: webpack

### 前端的三架马车

#### 渐进式框架: Vue

##### 单元测试

[一篇文章学会 Vue 项目单元测试 ------  @知乎 时长: 20分钟](https://zhuanlan.zhihu.com/p/48758013)

#### 用于构建用户界面的JavaScript库: React.JS

#### 大而全的: angular8

#### MVC 与 MVP 与 MVVM

### 值得一用的工具库

#### Lodash.JS

#### Ramda.JS
......

## JavaScript !!!

> 任何可以用 JavaScript 来写的应用，最终都将用 JavaScript 来写.

### node 后端框架: express, koa2, nest

### 使用 JavaScript, HTML 和 CSS 构建跨平台的桌面应用: Electron

### 使用JavaScript和React编写原生移动应用: React Native

### 物联网的框架: IoT.JS

### 深度学习: TensorFlow.JS









