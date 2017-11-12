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
pre {
  color: #d5d3cb;
}  
</style>

## 说在前面的话

- 本文档是我学习Bootstrap时的练习笔记。
- 本文档内容来自[慕课网][imooc]和[Bootstrap中文网][Bootstrap中文网]。
- 本文档为了更方便的显示Bootstrap的样式效果，引入了bootstrap.min.css文件。

## 下载

- 下载[用于生产环境的Bootstrap](https://github.com/twbs/bootstrap/releases/download/v3.3.7/bootstrap-3.3.7-dist.zip)

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
## 实例

- 可以在这获取[Bootstrap源码][源代码],里面包含有实例。
- 可以在[Bootstrap中文网][Bootstrap中文网]获取更详细的说明。

[Bootstrap中文网]: <http://v3.bootcss.com/> (Bootstrap中文网)
[源代码]: <https://codeload.github.com/twbs/bootstrap/zip/v3.3.7> (官方实例)
[imooc]: <http://www.imooc.com/learn/141> (imooc)

## 正文

### 标题

- HTML 中的所有标题标签，``<h1> ``到 ``<h6>`` 均可使用。
- 另外还提供了 ``.h1``到 ``.h6`` 类，为的是给内联（inline）属性的文本赋予标题的样式。
- Bootstrap覆盖了标题的默认的样式，使其在所有浏览器下显示的效果一样。

源码如下
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
