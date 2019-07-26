---
title: 语法规范
date: 2019-07-24 11:52:58
tags:
---

语法规范  
> syntax  
> 英 [ˈsɪntæks] 美 [ˈsɪntæks]  
> n.句法; 句法规则[分析]; 语构; 语法;  

计算机里，经常出现这个错误，就是语法错误，一般来说就是自己写的不符合这种编程的语法
```js
const if = 123;// SyntaxError: Unexpected token if
{}.a;//SyntaxError: Unexpected token .
a()a;//SyntaxError: Unexpected identifier
if()a;//SyntaxError: Unexpected token )
……
```
--------------
# ESLint
有些规范建议直接在eslint设置规范
## indent 缩进
> indent  
> 英 [ɪnˈdent]   美 [ɪnˈdent]  
> vt.  切割…使呈锯齿状; 缩进排版;  
常用方式有
1. 一个tab（制表）
```js
if(true){
/*tab*/console.log("exec");
}
```
2. 四个space（空格）
```js
if(true){
    console.log("exec");
}
```
3. 两个space
```js
if(true){
  console.log("exec");
}
```
建议使用两个空格，理由是
* 用两个空格的人很多，并且在逐渐增加
* 层级多了，也只是一层2个，不会让横向过长

**eslint参数为**
```js
{
  "indent": ["error", 2]
}
```
## 分号
建议加分号，因为在很多情况下会有问题，尤其ASI
```js
a = b + c
(d + e).print()
//会解析成下面的
a = b + c(d + e).print();
//-------------
a = b
/hi/g.exec(c).map(d)
//会解析成下面的
a = b / hi / g.exec(c).map(d);
//-------------
someFunction()
['ul', 'ol'].map(x => x + x)
//会解析成下面的
const propKey = ('ul','ol'); // comma operator
assert.equal(propKey, 'ol');
someFunction()[propKey].map(x => x + x);
```
**eslint参数为**
```js
{
  'semi': ['error', 'always']
}
```
# 命名
## 变量以及属性的命名规则
必须是统一码(Unicode)
+ 字母:a-z,A-Z等
+ $,_
  + -不能用
+ 数字:0-9等
  + 不能以数字不能开头  
```js
const строка = '';
const ε = 0.0001;
let 变量 = 0.0001;
let _tmp = 0;
const $foo2 = true;
let 0a = 1;//SyntaxError: Invalid or unexpected token
let a-b = 1;//SyntaxError: Unexpected token -
```
*小贴士*：
不能用预留关键字做变量,比如if,ture,const  
但是可以做属性
```js
const if = 123;// SyntaxError: Unexpected token if
const obj = { if: 123 };
obj.if//123
```
所有js预留关键字
```
await break case catch class const continue debugger default delete do else export extends finally for function if import in instanceof let new return static super switch this throw try typeof var void while with yield
```
没有在js中使用，但是也预留的关键字
```
enum implements package protected interface private public
```
不是预留但是也要避免，他们本来就已经定义了关键字
```
Infinity NaN undefined async
```
虽然可以用，但是要避免用全局变量作为局部变量
```
String, Math, etc.
```
## 变量样式
+ 驼峰: threeConcatenatedWords
  + Camel case
+ 下划线(蛇形): three_concatenated_words
  + Underscore case (also called snake case)
+ 横线(肉串): three-concatenated-words
  + Dash case (also called kebab case)

我们变量一般选用驼峰，因为看起来简洁，也比下划线少打一些字  
文件名，我们选择用横线，因为windows不区分大小写，比如git上提交的两个文件是myFile和myfile，在unix类的系统没事，但是在windows下会报错
```ssh
my-module.js
```
## 大小写
首字母小写
```js
let myVar;//变量
function myFunction(){}//函数
let obj = {};
obj.myMethod//方法
```
首字母大写
```js
class MyClass {}//类
```
大写加下划线
```js
const EVENT_START = "事件开始"//常量
```
css请用肉串样式
```css
special-class:{}
```
```html
<div class="special-class"></div>
```
## 下划线
成员变量
```js
class MyClass{
  construct(
    this._memberVar = 1;
  );
}
```
实体元素写两个下划线，就是在场景中实际存在的内容
```js
class MyClass{
  construct(
    this.__element = document.getElementById("elementID");
  );
}
```
