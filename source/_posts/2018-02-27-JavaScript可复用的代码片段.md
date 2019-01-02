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

## 分流

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
// 模拟调用
function RandomNumBoth (Min, Max) {
      var Range = Max - Min
      var Rand = Math.random()
      var num = Min + Math.round(Rand * Range) //四舍五入
      return num
}
shunt ( obj, RandomNumBoth(1, 3) )
```

```js
let x = {
    'b': 'love',
    'c': 1
}

if (x['b'] === 'love') {
    return 'you'
} else if (x['b'] === 'apple') {
    if (x['c'] % 2 === 1) {
        x.g = 233
        return 'odd'
    }
} else {
    return 'something'
}

let a = function(o) {
    return {
        // 倒写
        __default__: () = >'something',
        [o['b'] === 'apple'] : {
            __other__: () = >{
                x.g = 233
            },
            [o['c'] % 2 === 1] : () = >'odd'
        },
        [o['b'] === 'love'] : () = >'you'
    }
}

let obj = a(x)

let shunt = function(o) {
    o['__other__'] && o['__other__']()
    if (is.function(o[true])) return o[true]()
    if (!is.object(o[true]) && is.function(o['__default__'])) return o['__default__']()
    return shunt(o[true])
}

shunt(obj)
```

