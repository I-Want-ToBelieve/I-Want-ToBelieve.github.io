---
title: Bootstrap语法一览
date: 2017-11-11 18:11:53
tags:
- 笔记
- Bootstrap
categories:
- 笔记
- BootstrapV3.3.7
---

![bootstrap][bootstrap.png]

[bootstrap.png]: <http://oy9dwtsnx.bkt.clouddn.com/bootstrap.png> (bootstrap.png)


本文最后迭代于

## 说在前面的话


- 本文档是我学习Bootstrap时的练习笔记。
- 本文档内容来自[慕课网][imooc]和[Bootstrap中文网][Bootstrap中文网]。
- 本文档为了更方便的显示Bootstrap的样式效果，引入了bootstrap.min.css文件
(bootstrap减小了的行间距，这看起来很拥挤)。

## 下载

- 下载[用于生产环境的Bootstrap](https://github.com/twbs/bootstrap/releases/download/v3.3.7/bootstrap-3.3.7-dist.zip)

- CDN加速

<!-- more -->

```html
<!-- 最新版本的 Bootstrap 核心 CSS 文件 -->
<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- 可选的 Bootstrap 主题文件（一般不用引入） -->
<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

<!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
<script src="https://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
```

### 通过 Bower 进行安装

还可以通过 Bower 安装并管理 Bootstrap 的 Less、CSS、JavaScript 和字体文件。
``$ bower install bootstrap``

### 通过 npm 进行安装

你还可以利用 npm 工具来安装 Bootstrap：
``$ npm install bootstrap@3``

## 基本模板

拷贝并粘贴下面给出的 HTML 代码，这就是一个最简单的 Bootstrap 页面了。
```HTML
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="https://cdn.bootcss.com/html5shiv/3.7.3/html5shiv.min.js"></script>
      <script src="https://cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>你好，世界！</h1>

    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="bootstrap/js/bootstrap.min.js"></script>
  </body>
</html>
```
在上面的模板中，由于bootstrap依赖jquery库，所以在引入bootstrap之前必须先引入jquery
<!--more-->
## 实例

- 可以在这获取[Bootstrap源码][源代码],里面包含有实例。
- 可以在[Bootstrap中文网][Bootstrap中文网]获取更详细的说明。

[Bootstrap中文网]: <http://v3.bootcss.com/> (Bootstrap中文网)
[源代码]: <https://codeload.github.com/twbs/bootstrap/zip/v3.3.7> (官方实例)
[imooc]: <http://www.imooc.com/learn/141> (imooc)

## 正文


{% fold 点击显示/隐藏 %}
由于引入了 **bootstrap.min.js** 的缘故，导致折叠功能定位异常，具体原因暂不知。
{% endfold %}



### HTML5 文档类型

{% note info %}
 Bootstrap 使用到的某些 HTML 元素和 CSS 属性需要将页面设置为 HTML5 文档类型。在你项目中的每个页面都要参照下面的格式进行设置。
{% endnote %}

如下 **↓**

```html
<!DOCTYPE html>
<html lang="zh-CN">
  ...
</html>
```

### 移动设备优先

{%note warning%}
为了确保适当的绘制和触屏缩放，需要在 ``<head>`` 之中添加 viewport 元数据标签。
{%endnote%}


如下 **↓**
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

{% note info %}
在移动设备浏览器上，通过为视口（viewport）设置 meta 属性为 user-scalable=no 可以禁用其缩放（zooming）功能。这样禁用缩放功能后，用户只能滚动屏幕，就能让你的网站看上去更像原生应用的感觉。注意，这种方式我们并不推荐所有网站使用，还是要看你自己的情况而定！
{% endnote %}

如下 **↓**
```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```

### 布局容器

{% note info %}
Bootstrap 需要为页面内容和栅格系统包裹一个 ``.container ``容器。我们提供了两个作此用处的类。注意，由于`` padding `` 等属性的原因，这两种 容器类不能互相嵌套。
{% endnote %}

- .container 类用于固定宽度并支持响应式布局的容器。

```html
<div class="container">
  ...
</div>
```

- .container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器。

```html
<div class="container-fluid">
  ...
</div>
```

### [栅格系统](http://v3.bootcss.com/css/#grid)



### 排版

#### 标题

- HTML 中的所有标题标签，``<h1> ``到 ``<h6>`` 均可使用。
- 另外还提供了 ``.h1``到 ``.h6`` 类，为的是给内联（inline）属性的文本赋予标题的样式。
- Bootstrap覆盖了标题的默认的样式，使其在所有浏览器下显示的效果一样。

css源码如下

{% fold 点击显示/隐藏 %}
```css
/*bootstrap.css
  line:1174-1288
*/
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 20px;
  margin-bottom: 10px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 10px;
  margin-bottom: 10px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 36px;
}
h2,
.h2 {
  font-size: 30px;
}
h3,
.h3 {
  font-size: 24px;
}
h4,
.h4 {
  font-size: 18px;
}
h5,
.h5 {
  font-size: 14px;
}
h6,
.h6 {
  font-size: 12px;
}
```
{% endfold %}


</br>

阅读bootstrap.css源码可以发现Bootstrap对标题样式进行了以下显著的优化重置：

1. 重新设置了margin-top和margin-bottom的值。
h1~h3重置后的值都是20px；h4~h6重置后的值都是10px。

2. 所有标题的行高都是1.1（也就是font-size的1.1倍）。
而且文本颜色和字体都继承父元素的颜色和字体。

3. 固定不同级别标题字体大小。
h1=36px，h2=30px，h3=24px，h4=18px，h5=14px和h6=12px。

<div style="float:left">
```html
<h1>h1. Bootstrap heading</h1>
<h2>h2. Bootstrap heading</h2>
<h3>h3. Bootstrap heading</h3>
<h4>h4. Bootstrap heading</h4>
<h5>h5. Bootstrap heading</h5>
<h6>h6. Bootstrap heading</h6>
```
</div>
```html
<div class="h1">h1. Bootstrap heading</div>
<div class="h2">h2. Bootstrap heading</div>
<div class="h3">h3. Bootstrap heading</div>
<div class="h4">h4. Bootstrap heading</div>
<div class="h5">h5. Bootstrap heading</div>
<div class="h6">h6. Bootstrap heading</div>
```
以上代码的呈现效果是一致的，如下

<div class="h1">h1. Bootstrap heading</div>
<div class="h2">h2. Bootstrap heading</div>
<div class="h3">h3. Bootstrap heading</div>
<div class="h4">h4. Bootstrap heading</div>
<div class="h5">h5. Bootstrap heading</div>
<div class="h6">h6. Bootstrap heading</div>

</br>
#### 副标题

- 在标题内还可以包含 ``<small>`` 标签或赋予 ``.small`` 类的元素，可以用来标记副标题。

bootstrap.css中也重置了 **副标题small** 的样式
1. 行高都是1，而且``font-weight``设置了``normal``变成了常规效果（不加粗），同时颜色被设置为灰色（``#999``）。

2. 由于<small>内的文本字体在h1~h3内，其大小都设置为当前字号的65%；而在h4~h6内的字号都设置为当前字号的75%；

```html
<h1>h1. Bootstrap heading <small>Secondary text</small></h1>
<h2>h2. Bootstrap heading <small>Secondary text</small></h2>
<h3>h3. Bootstrap heading <small>Secondary text</small></h3>
<h4>h4. Bootstrap heading <small>Secondary text</small></h4>
<h5>h5. Bootstrap heading <small>Secondary text</small></h5>
<h6>h6. Bootstrap heading <small>Secondary text</small></h6>
```
```html
<div class="h1">h1. Bootstrap heading<small>Secondary text</small></div>
<div class="h2">h2. Bootstrap heading<small>Secondary text</small></div>
<div class="h3">h3. Bootstrap heading<small>Secondary text</small></div>
<div class="h4">h4. Bootstrap heading<small>Secondary text</small></div>
<div class="h5">h5. Bootstrap heading<small>Secondary text</small></div>
<div class="h6">h6. Bootstrap heading<small>Secondary text</small></div>
```


以上代码的呈现效果是一致的，如下

<div class="h1">h1. Bootstrap heading<small>Secondary text</small></div>
<div class="h2">h2. Bootstrap heading<small>Secondary text</small></div>
<div class="h3">h3. Bootstrap heading<small>Secondary text</small></div>
<div class="h4">h4. Bootstrap heading<small>Secondary text</small></div>
<div class="h5">h5. Bootstrap heading<small>Secondary text</small></div>
<div class="h6">h6. Bootstrap heading<small>Secondary text</small></div>

#### 页面主体

##### 段落

{% note info  %}
Bootstrap 将全局 ``font-size`` 设置为 ``14px``，``line-height`` 设置为 ``1.428``(``20px``)。这些属性直接赋予 ``<body>`` 元素和所有段落元素。另外，``<p>`` 元素还被设置了等于 1/2 行高（即 ``10px``）的底部外边距（``margin``）。
{% endnote %}

如：

```html
<p>this is p one</p>
<p>this is p two</p>
```

显示效果：

<p>this is p one</p>
<p>this is p two</p>


##### 中心内容

- 通过添加 .lead 类可以让段落突出显示。

如下

```html
<p class="lead">
Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus.
</p>
```

编译为

<p class="lead">
Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus.
</p>

##### **内联文本元素**

###### **Marked text**

- 要突出显示在另一个上下文中关联的一连串文本，请使用``<mark>``标签。

如

```html
You can use the mark tag to <mark>highlight</mark> text.
```
显示为：

You can use the mark tag to <mark>highlight</mark> text.


###### **被删除的文本**

- 对于被删除的文本使用 ``<del>`` 标签。

如
```html
<del>This line of text is meant to be treated as deleted text.</del>
```
显示为

<del>This line of text is meant to be treated as deleted text.</del>



###### **无用文本**

- 对于没用的文本使用 ``<s>`` 标签。

如
```html
<s>This line of text is meant to be treated as no longer accurate.</s>
```
显示为

<s>This line of text is meant to be treated as no longer accurate.</s>

###### **插入文本**

- 额外插入的文本使用 ``<ins>`` 标签。

如
```html
<ins>This line of text is meant to be treated as an addition to the document.</ins>
```
显示为

<ins>This line of text is meant to be treated as an addition to the document.</ins>

###### **带下划线的文本**

- 为文本添加下划线，使用 <u> 标签。

如
```html
<u>This line of text will render as underlined</u>
```
显示为

<u>This line of text will render as underlined</u>

{% note warning %}
``<del>`` 与 ``<s>`` 和 ``<ins>`` 与 ``<u>`` 并无本质区别，仅只语义上的区别，标准如此，不要混用！
{% endnote %}

###### **小号文本**

- 对于不需要强调的``inline`` （行）或``block`` （快）类型的文本，使用 ``<small>`` 标签包裹，其内的文本将被设置为 **父容器字体大小** 的 ``85%``。标题元素中嵌套的 ``<small>`` 元素被设置 ``不同`` 的 ``font-size``。

- 你还可以为行内元素赋予 .small 类以代替任何 <small> 元素。

如
```html
<small>This line of text is meant to be treated as fine print.</small>
<div class=".small" >This line of text is meant to be treated as fine print.</div>
```
显示为

<small>This line of text is meant to be treated as fine print.</small>
<small>This line of text is meant to be treated as fine print.</small>

###### **着重（强调）**

- 通过增加 ``font-weight`` 值强调一段文本。


如
```html
<strong>rendered as bold text</strong>
```
显示为

<strong>rendered as bold text</strong>

###### **斜体**

- 用斜体强调一段文本。


如
```html
<em>rendered as italicized text</em>
```
显示为

<em>rendered as italicized text</em>

{% note primary %}
Alternate elements(替换元素)
在 HTML5 中可以放心使用 ``<b>``和 ``<i> ``标签。``<b>`` 用于高亮单词或短语，不带有任何着重的意味；而 ``<i> ``标签主要用于发言、技术词汇等。
{% endnote %}

#### 对齐

- 通过文本对齐类，可以简单方便的将文字重新对齐。

如
```html
<p class="text-left">Left aligned text.</p>
<p class="text-center">Center aligned text.</p>
<p class="text-right">Right aligned text.</p>
<p class="text-justify">Justified text合理的文本.</p>
<p class="text-nowrap">No wrap text不自动换行的文本.</p>
```

显示为：
<p class="text-left">Left aligned text.</p>
<p class="text-center">Center aligned text.</p>
<p class="text-right">Right aligned text.</p>
<p class="text-justify">Justified text合理的文本.</p>
<p class="text-nowrap">No wrap text不自动换行的文本.</p>

#### 改变大小写

- 通过这几个类可以改变文本的大小写。

如
```html
<p class="text-lowercase">Lowercased text.</p>
<p class="text-uppercase">Uppercased text.</p>
<p class="text-capitalize">Capitalized text.</p>
```
显示为：

<p class="text-lowercase">Lowercased text.</p>
<p class="text-uppercase">Uppercased text.</p>
<p class="text-capitalize">Capitalized text.</p>

#### 列表


##### **无样式列表**

- 移除了默认的 ``list-style`` 样式和左侧外边距的一组元素（只针对直接子元素）。**这是针对直接子元素的** ，也就是说，你需要对所有嵌套的列表都添加这个类才能具有同样的样式。

如
```html
<ul class="list-unstyled">
  <li>...</li>
  <li>...</li>
  <li>...</li>
  <li>...</li>
</ul>
```
显示为

<ul class="list-unstyled">
  <li>...</li>
  <li>...</li>
  <li>...</li>
  <li>...</li>
</ul>


##### **内联列表**

- 通过设置 display: inline-block; 并添加少量的内补（padding），将所有元素放置于同一行。

如
```html
<ul class="list-inline">
  <li>Lorem ipsum</li>
  <li>Phasellus iaculis </li>
  <li>Nulla volutpat</li>
  <li>...</li>
</ul>
```
显示为

<ul class="list-inline">
  <li>Lorem ipsum</li>
  <li>Phasellus iaculis </li>
  <li>Nulla volutpat</li>
  <li>...</li>
</ul>

##### **描述**

- 带有描述的短语列表。

如
```html
<dl>
  <dt>描述列表</dt>
  <dd>描述列表对于定义术语来说是完美的。</dd>
</dl>
```
显示为

<dl>
  <dt>描述列表</dt>
  <dd>描述列表对于定义术语来说是完美的。</dd>
</dl>

##### **水平排列的描述**

- ``.dl-horizontal`` 可以让`` <dl> ``内的短语及其描述排在一行。开始是像 ``<dl>`` 的默认样式堆叠在一起，随着导航条逐渐展开而排列在一行。

如
```html
<dl class="dl-horizontal">
  <dt>Description lists</dt>
  <dd>A description list is perfect for defining terms.</dd>
</dl>
```
显示为

<dl class="dl-horizontal">
  <dt>Description lists</dt>
  <dd>A description list is perfect for defining terms.</dd>
</dl>

{% note primary %}
<span style="color: #6F42C1;"> **自动截断** </span>

通过 ``text-overflow`` 属性，水平排列的描述列表将会截断左侧太长的短语。在较窄的视口（viewport）内，列表将变为默认堆叠排列的布局方式。
{% endnote %}
















<script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script>

<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">


<style>
a {
  color: #3d3b3b;
}
a:hover
{
color: #3d3b3b;
text-decoration:none;
}
code {
   background-color: #2d2d2d;
   color: #fdfcf8;
}
br{
  display:none;
}


</style>
