---
title: JavaScript可复用的代码片段
date: 2018-02-27 21:31:42
tags:
- 笔记
- JavaScript
categories:
- 笔记
- JavaScript
---

## 使用命令对象替代Switch语句

```js
  var F = function ( name ) {
      var names = {
          '1': function() {
              return 'hack';
          },
          '2': function() {
              return 'slash';
          },
          '3': function() {
              return 'run';
          }
      };
      if (typeof names[name] !== 'function') {
          return false;
      }
      return names[name]();
 }
```

## 树状分流

```js
shunt (fo, fn) {
       if (typeof fo[fn] !== 'function') {
                return false
       }      
        return fo[fn]()
}
const obj = {
    1: function (){
        // do something
    },
    2: function (){
        // do something
	},
    3: function (){
        // do something
    }
}
// 辅助模拟调用
function RandomNumBoth (Min, Max) {
      var Range = Max - Min
      var Rand = Math.random()
      var num = Min + Math.round(Rand * Range) //四舍五入
      return num
}
shunt ( obj, RandomNumBoth(1, 3) )
```

