---
title: markdown
date: 2019-06-06 16:47:33
tags: markdown
---
markdown的使用
▸ 标题
▸ 段落
▸ 区块引用
▸ 代码区块
▸ 强调
▸ 列表
▸ 分割线
▸ 链接
▸ 图片
▸ 反斜杠
▸ 符号
▸ 表格
▸ 流程图


# 1. 标题
## 1.1. 使用= 和 -，标记一级和二级 标题。
### 代码
```
一级标题
=
二级标题
-
```
### 效果
> 一级标题
> =
> 二级标题
> -
## 1.2. 使用 #,可以表示 1-6级 标题。
### 代码
```
# 第一级标题 `<h1>` 
## 第二级标题 `<h2>` 
### 第三级标题 `<h3>` 
#### 第二四级标题 `<h4>` 
##### 第五级标题 `<h5>` 
###### 第六级标题 `<h6>` 
```
### 效果
> # 第一级标题 `<h1>` 
> ## 第二级标题 `<h2>` 
> ### 第三级标题 `<h3>` 
> #### 第二四级标题 `<h4>` 
> ##### 第五级标题 `<h5>` 
> ###### 第六级标题 `<h6>` 


# 2. 段落
段落的前后要有空行，所谓的空行是指没有文字内容。  
若想在段内强制换行的方式是使用两个以上空格加上回车（引用中换行省略回车）
### 代码
```
第一段文字¶¶↵第二段文字
```
### 效果
> 第一段文字  
> 第二段文字


# 3. 区块引用
在段落的每行或者只在第一行使用符号 > ,还可使用多个嵌套引用
### 代码
```
> 区块引用
>> 嵌套引用
>>> 三嵌套引用
>>>> 四嵌套引用
```
### 效果
> 区块引用
>> 嵌套引用
>>> 三嵌套引用
>>>> 四嵌套引用


# 4. 代码区块
代码区块的建立是在每行加上4个空格或者一个制表符（如同写代码一样）


使用‘\`’符号，可以添加语言种类



```java
fun main(args: Array<String>) {   
   println("Hello World!")   

   println("sum = ${sum(34, 67)}")  
   println("sum = ${sum(34, 67)}")  
   println("sum = ${sum(34, 6, 57, 34)}")  

   printSum(237, 57)  
   printSum(234, 567, 8)  
   vars(1, 4, 6, 78, 0, 6, 9, 8)  


   val sumLambda: (Int, Int) -> Int = { x, y -> x + y }  
   println("sumLambda = ${sumLambda(3, 6)}")  

   testFor()  


   val a: Int = 1000  
   println(a === a)//true 值相等，对象地址相等  

   //经过了装箱，创建了两个不同的对象  
   val boxedA: Int? = a  
   val anotherBoxedA: Int? = a  

   //虽然经过了装箱，但是值是相等的，都是10000  
   println(boxedA === anotherBoxedA) //  false，值相等，对象地址不一样  
   println(boxedA == anotherBoxedA) // true，值相等  
}  
```
注意⚠️：需要和普通段落之间存在空行！


支持的语言


名称	| 关键字
----|----
AppleScript	| applescript
ActionScript 3.0 | actionscript3, as3
Shell	| bash, shell
ColdFusion | coldfusion, cf
C	| cpp, c
C#	| c#, c-sharp, csharp
CSS	| css
Delphi |	delphi, pascal, pas
diff&patch |	diff patch
Erlang |	erl, erlang
Groovy |	groovy
Java	| java
JavaFX	| jfx, javafx
JavaScript |	js, jscript, javascript
Perl	| perl, pl, Perl
PHP	| php
text	| text, plain
Python	| py, python
Ruby	| ruby, rails, ror, rb
SASS&SCSS |	sass, scss
Scala	| scala
SQL	| sql
Visual | Basic	vb, vbnet
XML	| xml, xhtml, xslt, html
Objective C |	objc, obj-c
F#	| f#, f-sharp, fsharp
R	| r, s, splus
matlab	| matlab
swift	| swift
GO	| go, golang


# 5. 强调
在强调内容两侧分别加上 *或者 -
### 代码
```
*斜体* ，_斜体_
**加粗**，__粗体__
```
### 效果
> *斜体* ，_斜体_  
> **加粗**，__粗体__


# 6. 列表
## 无序
使用 . 、+、或- 标记无序列表
### 代码
```
-   第一项
+   第二项
-   第三项
+   第四项
-   第五项
+   第六项
```
### 效果
> -   第一项
> +   第二项
> -   第三项
> +   第四项
> -   第五项
> +   第六项   

**注意：标记后面最少有一个_空格_或_制表符_。若不在引用区块
中，必须和前方段落之间存在空行
## 有序
### 代码
```
1. 第一项
2. 第二项
3. 第三项
4. 第四项
5. 第五项
6. 第六项
```
### 效果
> 1. 第一项
> 2. 第二项
> 3. 第三项
> 4. 第四项
> 5. 第五项
> 6. 第六项


# 7. 分割线
分割线最常使用就是三个或以上的 * ， ======还可以使用  - 和 _
### 代码
```
***
---
_____ 
======
```
### 效果
> ***
> ---
> _____ 
> =======


# 8. 链接
## 行内式
### 代码
```
[GitHub](http://github.com)
自动生成连接  <http://www.github.com/>
```
### 效果
> [GitHub](http://github.com)  
> 自动生成连接  <http://www.github.com/>
## 参考式
### 代码
```
[GitHub][1]
[1]:http://github.com
自动生成连接  <http://www.github.com/>
```
### 效果
> [GitHub][1]  
> [1]:http://github.com  
> 自动生成连接  <http://www.github.com/>

注意：上述的 [1]:http://github.com 不出现在区块中


# 9. 图片
添加图片形式和链接相似，只需要在链接的基础上前方加一个 ！号
### 代码
```
![GitHub set up](http://zh.mweb.im/asset/img/set-up-git.gif)
//格式: ![Alt Text](url)
```
### 效果
> ![GitHub set up](http://zh.mweb.im/asset/img/set-up-git.gif)


# 10. 反斜杠 '\\'
相当于反转义作用。使符号成为普通符号


# 11. 符号 ``
起到标记作用，如标签：  
Ctrl+A 、Ctrl+C、Ctrl+V


# 12. 表格
```
第一格表头 | 第二格表头
---------| -------------
内容单元格 第一列第一格 | 内容单元格第二列第一格
内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格
内容单元格 第一列第三格 多加文字 | 内容单元格第二列第三格
内容单元格 第一列第四格 多加文字 | 内容单元格第二列第四格
```
### 效果
> 第一格表头 | 第二格表头
> ---------| -------------
> 内容单元格 第一列第一格 | 内容单元格第二列第一格
> 内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格
> 内容单元格 第一列第三格 多加文字 | 内容单元格第二列第三格
> 内容单元格 第一列第四格 多加文字 | 内容单元格第二列第四格


# 13. 流程图
```
st=>start: Start:>https://www.jpjbp.com/
io=>inputoutput: verification
op=>operation: Your Operation
cond=>condition: Yes or No?
sub=>subroutine: Your Subroutine
e=>end

st->io->op->cond
cond(yes)->e
cond(no)->sub->io
```
### 效果
st=>start: Start:>https://www.jpjbp.com/
io=>inputoutput: verification
op=>operation: Your Operation
cond=>condition: Yes or No?
sub=>subroutine: Your Subroutine
e=>end

st->io->op->cond
cond(yes)->e
cond(no)->sub->io

更多语法参考： [流程图语法参考](http://flowchart.js.org)