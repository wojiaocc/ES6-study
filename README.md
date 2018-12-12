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
ES5中，只存在全局作用域和函数作用域，由于 let的引入了块级作用域的概念。
**例子1：**
*代码如下所示：*
``` javascript
{
    var a=1;
    let b=2;
}
console.log(a);
console.log(b);
```
*控制台输出*
![image](https://github.com/wojiaocc/ES6-study/blob/master/images/err1.png)
由于let定义在块级作用域中，所以在全局下定义的b会报错，由var定义的a不会出现这种情况。