---
layout: post
title: JavaScript算法汇总
date: 2017-10-31 20:31:33
tags:
- 笔记
- JavaScript
categories:
- 笔记
- JavaScript算法汇总
---

## 转换HTML实体（Convert HTML Entities）
- 将字符串中的字符 `&`、`<`、`>`、`"` （双引号）, 以及 `'` （单引号）转换为它们对应的 HTML 实体。
```JavaScript
function convert(str) {

  // &colon;&rpar;
  // 声明一个存储字符与其对应的HTML实体代码的对象
  var entityMap = {
    '&': '&amp;',
    '<': '&lt;',
    '>': '&gt;',
    '\"': '&quot;',
    '\'': '&apos;',
  };

  //使用string的replace方法，将用正则匹配到的字符替换成entityMap对象中相对应的的属性值
  return str.replace(/[&<>"']/g,function(matched){
    return entityMap[matched];
  });
}

convert("Dolce & Gabbana");
```
可以在下面这个网站查询到符号对应的HTML实体代码

[Character Entity Reference Chart](https://dev.w3.org/html5/html-author/charref "Character Entity Reference Chart")
 <!--more-->
## 判断素数 (isPrimes?)
```JavaScript
function sumPrimes(num) {
  var tem = num;
  num =0;
  // 声明一个最基础的素数数组
  var primeNumber = [2];
  // 判断从3到num 之间的所以整数，将其中的素数添加到素数数组中。
  for(var i = 3; i <= tem; i++){
    // Array(i + 1).join.('1') 将i+1的值转换为由i个1组成的字符串：1111111.
    // 通过test()来判断 正则表达式/^.?$|^(..+?)\1+$/是否匹配成功
    /* /^.?$|^(..+?)\1+$/ 匹配子字符串'1'
    在字符串 Array(i + 1).join('1'))中的次数不为素数次*/
    if( !/^.?$|^(..+?)\1+$/.test(Array(i + 1).join('1'))){
       primeNumber.push(i);
    }
  }

  // 迭代累积素数数组，得到它们的和
  for(var x = 0; x < primeNumber.length; x++){
    num += primeNumber[x];
  }
  return num;
}

sumPrimes(10);
```
关于正则表达式，也许这能解释一二
[正则表达式 ^(?!(xx+)\1+$) 的含义？](https://www.zhihu.com/question/22571865/answer/21824402 "正则表达式 ^(?!(xx+)\1+$) 的含义？")

## 系统时间（System Time）

```html
<!DOCTYPE HTML>
<html>
<head>
<meta charset="utf-8"/>
<title>当前系统时间</title>
<script>
 window.onload = function(){
    showTime();
  }
  function showTime(){
    var now=new Date();
    var year=  now.getFullYear();
    var month=  now.getMonth()+1;
    var day = now.getDate();
    var h =  now.getHours();
    var m = now.getMinutes();
    var s =  now.getSeconds();
    m=m<10?"0"+m:m;
    s=s<10?"0"+s:s;

    var weekday='星期'+'日一二三四五六'.charAt(now.getDay());

    document.getElementById("show").innerHTML=""+year+"年"+month+"月"+day+"日 "+ weekday +h+":"+m+":"+s;
    t=setTimeout('showTime()',500);
  }

</script>
</head>
<body>
<div class="content1">
  <div id="show">显示时间的位置</div>
  <!-- 2017年12月12日 星期二 24:00:00-->
</div>
</body>
</html>
```

## JS生成某区间随机数

### min ≤ r ≤ max

```js
function RandomNumBoth(Min,Max){
      var Range = Max - Min;
      var Rand = Math.random();
      var num = Min + Math.round(Rand * Range); //四舍五入
      return num;
}
```

### min ≤ r < max

```js
function RandomNum(Min, Max) {
      var Range = Max - Min;
      var Rand = Math.random();
      var num = Min + Math.floor(Rand * Range); //舍去
      return num;
}
```

### min < r ≤ max

```js
function RandomNum(Min, Max) {
      var Range = Max - Min;
      var Rand = Math.random();
      if(Math.round(Rand * Range)==0){       
        return Min + 1;
      }
      var num = Min + Math.round(Rand * Range);
      return num;
}
```

### min < r < max

```js
function RandomNum(Min, Max) {
      var Range = Max - Min;
      var Rand = Math.random();
      if(Math.round(Rand * Range)==0){
        return Min + 1;
      }else if(Math.round(Rand * Max)==Max)
      {
        index++;
        return Max - 1;
      }else{
        var num = Min + Math.round(Rand * Range) - 1;
        return num;
      }
 }
```
