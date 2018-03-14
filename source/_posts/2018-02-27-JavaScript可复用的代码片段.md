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

```
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
