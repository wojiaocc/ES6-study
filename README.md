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

# let 
ES5中，只存在全局作用域和函数作用域，由于 let的引入 