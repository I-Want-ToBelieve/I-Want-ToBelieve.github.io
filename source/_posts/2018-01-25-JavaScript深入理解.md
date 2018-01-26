---
title: JavaScript深入理解
date: 2018-01-25 01:00:17
tags:
- 笔记
- JavaScript
categories:
- 笔记
- JavaScript
---


## 立即执行函数 模拟块级作用域（私有作用域）

这是一种常用的写法（起手式），将匿名函数用括号括起来形成函数表达式
在该函数表达式后使用括号立即调用该函数表达式
前面的分号，是为了避免代码压缩后，前边的代码结尾没写分号。

使用立即执行函数 模拟出来的块级作用域，可以避免污染全局变量
而且还可以减少闭包占用的内存问题，因为没有指向匿名函数的引用，
只要函数执行完毕，就可以立即销毁其作用域了。

```js
;( function( args ) {
  'use strict'
  // 这里是块级作用域（私有作用域）
} )( args );
```

## 私有变量 静态私有变量

利用 构造函数的块级作用域 实现私有变量
```js
function ObjName() {
  // 函数内部的私有变量
  var privateVariable = 10;
  // 私有函数
  function privateFunction(num) {
    // do something
    num++;
    return num;
  }

  // 公有、特权方法 有权访问私有变量和函数
  this.publicMethod = function () {
    // 访问私有变量 自加一
    privateVariable++;
    // 调用私有函数 并return结果
    return privateFunction(privateVariable);
  };
  this.getPrivateVariable = function() {
    return PrivateVariable;
  }
}

var instance = new ObjName();
// 私有变量、函数，外界无法直接访问、调用
instance.privateVariable; // undefined
instance.privateFunction(); // TypeError: instance.privateFunction is not a function

// 使用 公开的特权函数 间接操纵
instance.getPrivateVariable(); //10
instance.publicMethod(); // 12
// 再实例化一个对象
var oo = new ObjName();
// 结果返回 10
oo.getPrivateVariable(); // 10

```

利用 立即执行函数的块级作用域 实现<span class="fontred">静态</span>私有变量

```js
// defind 定义
;(function () {
  // 私有变量、函数
  var privateVariable = 10;

  function privateFunction(num) {
    // do something
    num++;
    return num;
  }
  // 全局构造函数 不能使用 Var 声明
  ObjName = function() {};

  // 共有、特权函数
  ObjName.prototype.publicMethod = function () {
    // 访问私有变量 自加一
    privateVariable++;
    // 调用私有函数 并return结果
    return privateFunction(privateVariable);
  };
  ObjName.prototype.getPrivateVariable = function () {
    return privateVariable;
  };
})();

// use 使用
var o = new ObjName();
o.privateVariable; // undefined
o.privateFunction(); // TypeError: o.privateFunction is not a function
o.getPrivateVariable(); // 10;
o.publicMethod(); // 12

// 再实例化一个对象
var oo = new ObjName();
// 结果返回 12 而不是初始值 10 说明访问的是 o 修改后的变量（同一个变量 静态变量）。
oo.getPrivateVariable(); // 12
```
由于公有函数定义在构造函数的原型对象上，所有实例将共享所有的私有成员。


## 单例模式与模块模式

JavaScript中，用对象字面量的方式实现单例模式：

```js
// 单例模式
var ObjName = {
  name: value,
  method: fucntion () {
    // do something
  }
};
```

在此基础上，声明私有变量、函数，并返回一个包含有私有变量、函数映射的匿名的公有单例对象就是模块模式了。

如下：

```js
// 以表达式的形式声明一个函数，以起到命名空间的作用
var ObjName = function () {
  // 声明私有成员
  var privateVariable = 10;

  function privateFunction() {
    // do something  
  }

  // return 一个包含有私有变量、函数映射的匿名的公有单例对象
  return {
    getPrivateVariable : function () {
      return privateVariable;
    },
    publicMethod :  function () {
      privateVariable++;
      return privateFunction();
    }
  }
}

// 此时ObjName是一个全局函数，我们可以直接调用它
var o = window.ObjName();
// or var o = ObjName();
o.getPrivateVariable();
o.publicMethod();

```

### 增强的模块模式

如下：

```js
// 以表达式的形式声明一个函数，以起到命名空间的作用
var ObjName = function () {
  // 声明私有成员
  var privateVariable = 10;

  function privateFunction() {
    // do something  
  }

  // 实例化一个自定义对象 我们将对这个对象进行增强
  var obj = new CustomType();
  // 添加特权、公有属性、方法
  obj.publicVariable = 1;
  obj.publicMethod = function () {
    privateVariable++;
    return privateFunction();
  }
  // return 增强后的对象
  return obj;
}

// 此时ObjName是一个全局函数，我们可以直接调用它
var o = window.ObjName();
// or var o = ObjName();
o.getPrivateVariable();
o.publicMethod();

```

```




## 构造函数模式+原型模式实现自定义类型（类）

```js
'use strict'
// define 定义 类
function ObjName( arg0,arg1,... ){
  this.arg0 = arg0;
  this.arg1 = arg1;
  ...
  this.arr = ["value0","value1",...]
  ...
}

ObjName.prototype = {
  // 将constructor指针指回自身 保证 instanceof字符以及isPrototpeOf() 判断的正确性
  constructor : ObjName,
  functionName : function(){
    // do something
  },
  functionName1 : function(){
    // do something
  }
  ...  
}

// use 使用 类实例
var instance = new ObjName( arg0,arg1,... );
var newArr = instance.arr;
instance.functionName0();
...

```


## 构造函数模式+动态原型模式实现自定义类型（类）

```js
'use strict'
// define 定义 类
function ObjName( arg0,arg1,... ){
  this.arg0 = arg0;
  this.arg1 = arg1;
  ...
  this.arr = ["value0","value1",...]
  ...
  if( typeof this.functionName0 !== 'function' ){
    /* 使用动态原型模式时，不能使用对象字面量重写原型对象。
    因为这会切断实例对象与其构造函数的原型对象的联系。*/
    ObjName.prototype.functionName0 = function() {
      // do something
    };
    ObjName.prototype.functionName1 = function() {
      // do something
    };
    ...
  }
}

// use 使用 类实例
var instance = new ObjName( arg0,arg1,... );
var newArr = instance.arr;
instance.functionName0();
...

```

## 构造函数模式+原型模式实现继承（组合继承）

```js
'use strict'
// define SuperType 定义 父类
function SuperType( arg0,arg1,... ) {
  this.arg0 = arg0;
  this.arg1 = arg1;
  ...
  this.arr = ["value0","value1",...]
}

// define SuperType prototype function 定义 父类的原型对象的属性函数
SuperType.prototype.superTypeFunctionName10 = function() {
  // do something
}
SuperType.prototype.superTypeFunctionName11 = function() {
  // do something
}
...

// define SubTypeType 定义 子类
function SubTypeType( arg0,arg1,arg2,... ) {
  SuperType.call( this,arg0,arg1,... );
  // or SuperType.apply(this,arguments);
  this.arg2 = arg2;
}

// SubTypetype prototype 指向 SuperType 的实例对象 形成原型链 实现继承
SubTypeType.prototype = new SuperType();
// 构造函数指针指回自己 保证 instanceof字符以及isPrototpeOf() 判断的正确性
SubTypeType.prototype.constructor = SubTypeType;


// define SubTypeType prototype function 定义 子类的原型对象的属性函数
SubTypeType.prototype.SubTypeFunctionName0 = function() {
  // do something
}
SubTypeType.prototype.SubTypeFunctionName1 = function() {
  // do something
}

// use 使用 继承父类后的子类 类实例
var instance = new SubTypeType( arg0,arg1,arg2,... );
var newArr = instance.arr;
instance.superTypeFunctionName10();
instance.SubTypeFunctionName0();
...

```

由于组合式继承 调用了两次父类的构造函数，有稍稍稍微的内存损耗。
就有了如下 **寄生组合式继承**

## 构造函数模式+寄生动态原型模式实现继承（寄生组合式继承）

```js
'use strict'
function inheritPrototype( SubType, SuperType ) {  
    /*这里为何需要调用object函数去构造一个新的对象，而不直接让SubType.prototype=SuperType.prototype呢？
    原因是如果这么做的话，当我们想给SubType的prototype里面添加共享属性或者方法时，
    如果其prototype指向的是SuperType的prototype
    那么在SubType的prototype里添加的属性和方法也会反映在SuperType的prototype里面，
    这明显是不合理的，这样做的后果是当我们只想使用SuperType时，也能看见SubType往里面扔的方法和属性。
    所以需要每个构造函数都需要持有自己专用的prototype对象。*/  
    var prototype = object( SuperType.prototype );  
    prototype.constructor = SubType;  
    SubType.prototype = prototype;  
};  

function SuperType( arg0,... ) {  
    this.arg0 = arg0;  
    ...
    if( typeof SuperType.prototype.superTypeFunctionName10 !== "function" ) {  
        SuperType.prototype.superTypeFunctionName10 = function () {
          // do something
        };
        SuperType.prototype.superTypeFunctionName11 = function () {
          // do something
        };          
    }  
}  

function SubTypeType( arg0, arg1,... ) {  
    SuperType.call( this, arg0 );
    // or SuperType.apply( this,arguments );  
    this.arg1 = arg1;  

    if( typeof SuperType.prototype.superTypeFunctionName10 !== "function" ) {  
        SuperType.prototype.superTypeFunctionName10 = function () {
          // do something
        };
        SuperType.prototype.superTypeFunctionName11 = function () {
          // do something
        };          
    }
};  

// 调用 寄生继承函数
inheritPrototype( SubType, SuperType );  

// 使用
var instance = new Sub( arg0,arg1,... );  
instance.superTypeFunctionName10();  
instance.superTypeFunctionName11();
```

## 函数表达式之递归

```js
function factorial( num ) {
  if( num <= 1 ){
    return 1;
  }else{
    return num * factorial( num - 1 );
  }
}

// 这样调用会出错
var instance = factorial;
factorial = null;
instance(4); // erroe

// 使用 arguments.callee指向正在执行的函数
function factorial( num ) {
  if( num <= 1 ){
    return 1;
  }else{
    return num * arguments.callee( num - 1 );
  }
}

// 但是在严格模式下arguments.callee不能使用

// 使用 函数表达式 解决
var factorial = ( function f( num ) {
  if( num <= 1 ){
    return 1;
  }else{
    return num * f( num - 1 );
  }
} );
```

## 闭包

函数中的函数称为闭包函数。

### 释放被闭包占用的内存

```js

// 声明一个简单的闭包函数
function f( arg0 ) {
  return function( arg1 ) {
     return arg0 + arg1;
  }
}

// 创建函数
var tem = f(3);
// 调用函数
tem(5); // 8

/*
在匿名函数执行完成后
显示的将指向 return出来的匿名函数的 指针指向null
以释放因为闭包而占用的内存
*/
tem = null;
```

### 闭包只取得包含函数（或称外部函数）中任意变量的<span class="fontred">最后</span>一个值

```js
function f() {
  // 存放函数的数组
  var result = new Array();

  var i;
  for( i = 0; i < 10; i++ ){
    // 循环添加函数到数组
    result[i] = function () {
      return i;
    };
  }
  // 返回一个函数数组
  return result;
}


var fArr = f();

fArr[0](); // 10
fArr[1](); // 10
...
fArr[8](); // 10
fArr[9](); // 10
// 函数数组中的所有函数的 返回值 都为 10
```

给闭包函数添加闭包函数，让这个函数数组中的函数的返回值符合预期。如下：

```js
function f() {
  // 存放函数的数组
  var result = new Array();

  var i;
  for( i = 0; i < 10; i++ ){
    // 循环添加函数到数组
    result[i] = function ( num ) {
      // 再添加一个匿名的闭包函数
      return function() {
        return num;
      };
    }( i );
  }
  // 返回一个函数数组
  return result;
}


var fArr = f();

fArr[0](); // 0
fArr[1](); // 1
...
fArr[8](); // 8
fArr[9](); // 9
// 函数数组中的所有函数的 返回值 都为 10
```

### 闭包中的 this关键字 在<span class="fontred">非严格模式</span>下将指向 window 对象

如下
"
```js
var value = 'A';
var Obj = {
  value:"B",

  getValue: function () {
    return function () {
      return this.value;
    };
  }
}

// 调用 调用 getValue() 返回后的 匿名闭包函数
Obj.getValue()(); // A
```

返回的是 A 而不是预期中的 B
因为闭包中的 this关键字 在<span class="fontred">非严格模式</span>下将指向 window 对象
而不是它包含函数（外部函数）作用域中的 Obj 对象。

在严格模式（``'use strict'``）下会报错：typeError: this is undefined

要想得到预期效果，必须将包含函数（外部函数）作用域中的 Obj 对象
以变量的形式的传入闭包函数的作用域中。如下：

```js
var value = 'A';
var Obj = {
  value:"B",

  getValue: function () {
    var that = this;
    return function () {
      return that.value;
    };
  }
}

// 调用 调用 getValue() 返回后的 匿名闭包函数
Obj.getValue()(); // B
```
