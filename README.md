# ES6-study
自己整理的webpack学习


## 什么是ES6
ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准

## 正式使用ES6前的准备
Babel 是一个广泛使用的 ES6 转码器，可以将 ES6 代码转为 ES5 代码，从而在现有环境执行。

## 开始使用Babel编译ES6
**安装**
Babel可以使用npm安装，在终端中转到该文件夹后执行下述指令就可以完成安装。
```
# 安装
$ npm install --save-dev babel-cli
$ npm install --save-dev babel-preset-es2015
```
**编译**
输入 npm run build 进行编译。

# let 
## 块级作用域
ES5中，只存在全局作用域和函数作用域，由于 let的引入了块级作用域的概念。
**例子1：**<br>
*代码如下所示：*<br>
``` javascript
{
    var a=1;
    let b=2;
}
console.log(a);
console.log(b);
```
*控制台输出*<br>
![image](https://github.com/wojiaocc/ES6-study/blob/master/images/err1.png)<br>
由于let定义在块级作用域中，所以在全局作用域下的b会报错，由var定义的a不会出现这种情况。<br>
最简单的应用就是：
``` javascript
    var a=[];
    for(var i=0;i<10;i++){
        a[i]=function(){
            console.log(i);
        };
    }
    a[6](); //10    

    var a=[];
    for(let i=0;i<10;i++){
        a[i]=function(){
            console.log(i);
        };
    }
    a[6]();    //6    
```
引用let后，循环内形成了闭包，所以let定义的i不存在全局覆盖，所以输出为6；

## 不存在变量提升
var定义变量：可以先使用，后声明；而let定义变量：只可先声明，后使用。
``` javascript
    console.log(a)
    var a=1;
    
    console.log(b);
    let b=2;  
```
用var 声明的显示undefined，而 let声明的直接报错。

## 暂时性死区

``` javascript
    var tmp=123;
    if(true){
        tmp="abc";
        let tmp;
    }
```
代码中存在全局变量tmp，但是块级作用域内let又声明了一个局部变量tmp，导致后者绑定了块级作用域，所以在let声明变量前，对tmp赋值会报错。此即暂时性死区。<br>

**ES6规定暂时性死区和不存在变量提升就是为了减少运行时的错误，防止在变量声明前就使用这个变量，从而导致意料之外的行为。**

## 不允许重复声明
``` javascript
    function func (){
        let b=100;
        var b=10;
    }

    function add(num){
        let num;
        return num+1;
    }

    function another(){
        let a=10;
        let a=5;
    }
```

# const
const命令用来声明常量，一旦声明，值就不能发生改变。后面的特性与let十分相识。 const 本质上是给变量提供的存储地址中值不变动，但是对于对象来说，对象的参数可发生改变。

# 声明 变量的6种方法
ES5中，声明变量只存在两种方式var和functon.<br>
在ES6中新增了四种声明方式，let、const、import、class.

# 变量的解构赋值

## 数组解构
ES6 允许写成下面这样。
``` javascript
let [a, b, c] = [1, 2, 3];
相当于 let a =1,b=2,c=3;
```
## 对象解构
``` javascript
const node = {
  loc: {
    start: {
      line: 1,
      column: 5
    }
  }
};

let { loc, loc: { start }, loc: { start: { line }} } = node;
line // 1
loc  // Object {start: Object}
start // Object {line: 1, column: 5}
```
## 字符串解构
``` javascript
let [a,b,c,d,e]="hello";
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"
```
## 数值和布尔值解构
``` javascript
let {toString: s} = 123;
s === Number.prototype.toString // true

let {toString: s} = true;
s === Boolean.prototype.toString // true
```
## 函数参数解构
``` javascript
function add([x, y]){
  return x + y;
}

add([1, 2]); // 3
```