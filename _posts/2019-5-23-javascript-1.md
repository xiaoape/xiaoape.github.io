---
layout: post
title: js进阶之函数参数转化为真实数组
categories: javascript
description: js进阶之函数参数转化为真实数组
keywords: javascript,js,函数
---

实际参数在函数中我们可以使用 arguments 对象获得 （注：形参可通过 arguments.callee 获得），虽然 arguments 对象与数组形似，但仍不是真正意义上的数组。

我们可以通过数组的 slice 方法将 arguments 对象转换成真正的数组。

方法一：通过Array.prototype属性调用slice方法
``` javascript
var args = Array.prototype.slice.call(arguments);
```
Array 本身是没有 slice 方法，它的方法在 Array.prototype中，而我们在调用 slice 方法的时候，如果在 Array 本身没有找到 slice 方法的话，会通过它的原型链往上查找。

方法二：通过调用[]的slice方法
``` javascript
var args = [].slice.call(arguments, 0);
```
方法三：通过遍历arguments,返回数组
``` javascript
function toArray(){
    var args = []; 
    for (var i = 1; i < arguments.length; i++) { 
        args.push(arguments[i]); 
    } 
    return args;
}
```
注：一般的函数的 arguments.length 都在 10 以内，方法二有优势； 
方法二的代码量上也比第一种少，至少可以减小一点字节

实例：
``` javascript
function revse(){
    try{
        return Array.prototype.slice.call(arguments);
    }
    catch(e){
        var newarr=[];
        for(var i=arguments.length-1;i>=0;i--){ 
          //newarr.push(arguments[i]);
          newarr[i] = arguments[i]; //这样比push快？
        }
        return newarr;
    }
}      
var s = revse('a','b','c');
console.log(s); //["a", "b", "c"]
```
跟arguments问题相关题目
在某些场景下，需要将函数的 arguments 参数作为一个数组调用，但是 arguments 是一个奇异对象，所以试着将 arguments 转化为一个数组，例如下面例子：
``` javascript
function argToArr(){
    return [].slice.call(arguments, 0);
}
console.log(argToArr(1,2,3));    //[1,2,3]

function argToArr(){
    return Array.slice.call(arguments, 0);
}
console.log(argToArr(1,2,3));    //Uncaught TypeError: Cannot read property 'call' of undefined
```
这是为什么呢？
第二段代码报错是因为Array是构造函数，不是对象，打开控制台，输入 typeof Array，结果是 function。
slice()方法在其原型对象中，而[]就是Array的原型对象，在控制台中输入 Array.prototype，结果是[],所以第一段代码可以顺利执行。

第二段代码如下修改就可以了:
``` javascript
function argToArr(){
    return Array.prototype.slice.call(arguments, 0); // 改这一行
}
console.log(argToArr(1,2,3)); 
```
