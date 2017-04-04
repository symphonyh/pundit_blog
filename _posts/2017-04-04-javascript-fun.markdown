---
layout: post
title: js Function
date: 2017-04-04
comments: true
external-url:
categories: javascript
---

## JavaScript中的函数定义
 1、自定义函数
语法：

```
 function 函数名 ( 参数1,参数2,…. )
 {
 ...
 }
 或
 var 函数名 = function (参数1,参数2,…. )
 {
 ...
 }
```
>传入的参数是可选的, 传入数量没有限制，多余的参数会忽略。

2、 如何调用函数
函数可以通过其名字加上括号中的参数进行调用:`函数名()`


&sect;&nbsp; 自定义函数调用
```
function sayHello(name){
alert( name + "hello" );
}
sayHello("Tom");
```
&sect;&nbsp; 函数变量的调用
```
var sayHello = function(name){
alert( name + "hello" );
}
sayHello(" Tom ");

```

3、函数如何返回值
通过 `return` 关键字返回函数的值；函数在执行过 `return `语句后立即停止代码；因此，`return` 语句后的代码都不会被执行。


4、匿名函数

- 匿名函数的基本形式为:`(function(){...})();`
- 前面的括号包含函数体，**后面的括号就是给匿名函数传递参数并立即执行**；
- 匿名函数的作用是避免全局变量的污染以及函数名的冲突。
 

>匿名函数最大的用途是创建闭包（这是Javascript语言的特性之一），并且还可以构建命名空间，以减少全局变量的使用。

> 小括号`()`的作用:
小括号能把我们的表达式组合分块，并且每一块，也就是每一对小括号，都有一个返回值。这个返回值实际上也就是小括号中表达式的返回值。即：我们用一对小括号把匿名函数括起来的时候，**实际上小括号对返回的，就是一个匿名函数的Function 对象。**因此，小括号对加上匿名函数就如同有名字的函数般被我们取得它的引用位置了，在这个引用变量后面再加上**参数列表**，就会实现普通函数的调用形式。
简单来说就是小括号有返回值，也就是小括号内的函数或者表达式的返回值，所以说小括号内的function返回值等于小括号的返回值。


&sect;&nbsp; 书写方式1：调用函数，得到返回值,强制函数直接执行再返回一个引用，引用再去调用执行;

```
(function(x,y){
alert(x+y);
return x+y;
})(3,4); 
```
>注意尾部`)`的使用与方式2区别，这种方式也是很多库爱用的调用方式，如jQuery，Mootools。


&sect;&nbsp; 书写方式2：调用函数，得到返回值,强制运算符使函数调用执行;
```
(function(x,y){
alert(x+y);
return x+y;
}(3,4)); 
``` 
 
&sect;&nbsp; 书写方式3：使用void
```
void function(x) {
x = x-1;
alert(x);
}(9);
```
5、闭包
闭包说白了就是函数的嵌套，内层的函数可以使用外层函数的所有变量，即使外层函数已经执行完毕；（涉及Javascript作用域链）

```
function checkClosure(){
    var str = 'rain-man';
    setTimeout(
        function(){ alert(str); } //这是一个匿名函数
    , 2000);
}
checkClosure();
```
>说明：checkClosure函数的执行，在checkClosure的函数体内创建了一个变量str，在checkClosure执行完毕之后str并没有被释放，这是因为setTimeout内的匿名函数`function(){ alert(str);}`存在这对str的引用。待函数体内的匿名函数被执行完毕,str才被释放。

```
var rainman = (function(x , y){
    return x + y;
})(2 , 3);
```
>说明：在这里我们创建了一个变量`rainman`，并通过直接调用匿名函数初始化为`5`，这种小技巧有时十分实用。

```
var outer = null;
(function(){
    var one = 1;
    function inner (){
        one += 1;
        alert(one);
    }
    outer = inner;
})();
outer();    //2
outer();    //3
outer();    //4
```
>说明：这段代码中的变量`one`是一个局部变量（因为它被定义在一个函数之内），因此外部是不可以访问的。但是这里我们创建了`inner`函数，`inner`函数是可以访问变量`one`的；又将全局变量`outer`引用了`inner`，所以三次调用`outer`会弹出递增的结果。

 **注意：闭包允许内层函数引用父函数中的变量，但是该变量是最终值**

```html

  <body>
  <ul>
      <li>one</li>
      <li>two</li>
      <li>three</li>
      <li>one</li>
  </ul>
 
```
```js
var lists = document.getElementsByTagName('li');
for(var i = 0 , len = lists.length ; i < len ; i++){
    lists[ i ].onmouseover = function(){
        alert(i);    
    };
}
```
>说明：你会发现当鼠标移过每一个`<li>`;元素时，总是弹出`4`，而不是我们期待的元素下标。这是为什么呢？**最终值！**当mouseover事件调用监听函数时，首先在匿名函数`(function(){ alert(i); })`内部查找是否定义了 `i`，结果是没有定义；因此它会向上查找，查找结果是已经定义了，并且`i`的值是`4`（循环后的i值）；所以，最终每次弹出的都是`4`。

      修改后的代码如下：
```js
var lists = document.getElementsByTagName('li');
for(var i = 0 , len = lists.length ; i < len ; i++){
    (function(index){
        lists[ index ].onmouseover = function(){
            alert(index);    
        };                    
    })(i);
}
```


6、`javascript jQuery coffeescript` 中函数的书写方法

&sect;&nbsp; <a> Javascript </a>

```
 function 函数名 ( 参数1,参数2,…. )
 {
 ...
 }
 ```
 
 ```
 var 函数名 = function (参数1,参数2,…. )
 {
 ...
 }
```

```
var rainman = (function(x , y){
    return x + y;
})(2 , 3); // 匿名函数
```

&sect;&nbsp; <a> jQuery </a>

```
$(document).ready(function(){ //.. });


推荐写法：
$(function(){ });
 ```
> 注意:网页中的DOM结构绘制完后就执行;(可能DOM元素相关的东西并没有加载完),这里和`window.onload = function(){};` 不同，`jquery（）`可以写多个，并不要求网页所有内容加载完毕执行！


 这不就是一个匿名的函数吗？

```
（function($){...}）（jQuery）
```
它的形参比较奇怪，是`$`,这里主要是为了不与其它的库冲突。这样我们就比较容易理解第一个括号内的内容就是定义了一个匿名函数，我们在调用函数的时候，都是函数名后边加上括号以及实参，但是由于操作符的优先级我们定义的匿名函数也需要用`（）`括起来。
第一个括号表示定义了一个匿名函数，然后第二个函数表示为该函数传递的参数，整个结合起来意思就是，定义了一个匿名函数，然后又调用该函数，该函数的实参为`jQuery`。

这种方法多用于存放开发的插件，执行其中的代码时，`Dom`对象并不一定加载完毕;相当于：

```
function fun($){...};fun(jQuery);

```

&sect;&nbsp; <a> Coffeescript with jQuery </a>

js code:
```
(function($) {

})(jQuery);


```
to coffee:
```
(($) ->
  
) jQuery
```

js code:

```
$(function() {
  return console.log("DOM is ready");
});

```
to coffee:

```
$ ->
  console.log("DOM is ready")
```

js code:
```
$(".submit").click(function() {
  return console.log("submitted!");
});
```
to coffee:
```
$(".submit").click ->
  console.log("submitted!")
```