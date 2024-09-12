---
title: Js
published: 2024-09-11
description: 'Vue study'
image: ''
tags: [Demo, Example, Markdown, Fuwari]
category: 'study'
draft: false 
---

## 一、概念
一门客户端==脚本语言==
运行在客户端浏览器中的。每个浏览器都有JavaScript的解析引擎
脚本语言：不需要编译，直接就可以被浏览器解析执行
JavaScript = ECMAScript + JavaScript 自己特有的东西（BOM+DOM）
		客户端脚本语言的标准
## 二、功能
1. 可以来增强用户和html页面的交互过程，可以来控制html元素，让页面有一些动态效果，增强用户的体验
2. html 定义网页的内容
3. css 定义网页的布局
4. JavaScript 控制了网页的==行为==

## 三、基本语法
### 1、与html结合方式
#### 内部JS
定义<`script`>，标签体内容就是 js 代码           **eg**：`<script> alert("hello world!") </script>`
#### 外部JS
定义js文件，通过 src 属性引入外部的 js 文件     **eg：** `<script src="路径></spcript>`

***注意**
1. `<script>`可以定义在html页面的任何地方。但是定义的位置会影响执行顺序
2. `<script>`可以定义多个

### 2、注释
与java相同
### 3、数据类型
1. 原始数据类型（基本数据类型）：
	- number：数字            整数、小数、NaN(not a number 一个不是数字的数字类型)
	- string：字符串            javaScript中没有字符的概念
	- boolean：true false
	- null：一个对象为空的占位符
	- undefined：未定义。如果一个变量没有给初始化值，则会被默认赋值为undefined
使用==typedof== 返回数字类型
1. 引用数据类型：对象
### 4、变量
### 5、运算符
1. 一元运算符：只有一个运算数的运算符
	- ++   --   /   +（正号）  -（负号）
	注意：在JS中，如果运算数不是运算符所要求的类型，那么js引擎会自动的将运算数进行类型转换
	**eg：**其他类型转number
	- string 转 number：按照字面值转换。如果字面值不是数字，则转为NaN（不是数字的数字）
	- boolean 转 number：true 转为1 ， false 转为0
1. 算数运算符
2. 比较运算符
	比较方式：
	- 类型相同：直接比较
		- 字符串：以字典形式，逐个字符比较，直到得出大小为止
	- 类型不同：先进行类型转换，再比较
		- === 全等于，比较之前，先判断类型，如果类型不一样，则直接返回false，如果相同则进行下一步比较
4. 逻辑运算符
	- &&：与（短路）
	- ||：或（短路）
	- ！：非
		- 其他类型转boolean（==使用 !!==  ）：
			1. number：0 或 NaN 为假，其他为真
			2. string：除了空字符串为false，其他都true
			3. null & undefined：false
			4. 对象：所有对象都是true;
### 5、特殊语法
1. 语句以 ; 结尾，如果一行只有一条语句则 ； 可以省略
2. 变量的定义使用var ，也可以不用
- 用：局部变量
- 不用：全局变量
### 6、流程控制语句 
### 7、案例
```css
<head>
	<style>  //在 head 中使用css 设置样式
		td{
		border: 1px solid;
		}
	</style>
</head>
...
<body>

<script>
	<table align="center" >  //利用表格并设置整体位置
		for(var i = 1 ; i < = 100 ; i++){
			document.write("<tr>");  //建立行
				for(var j = 1 ; j < = i j++){
					document.write("<td"); //建立块
					document.write(i+" * "+j+" = "+(i * j));
					document.write("</td>");
				}
				//document.write("&nbsp;");
			}
			document.write("</tr>");
	</table>
</script>

</body>
```
## JavaScript对象
### Array
1. 创建
	-  var arr = new Array（元素列表）;  %% 两种静态赋值 %%
	- var arr = [ 元素列表];
	- var arr = new Array（默认长度）； %% 程序中动态赋值 %%
	- var arr = new Array（）;         %% 空数组 %%
2. 方法
	- join（参数）：将数组中的元素按照指定的==分隔符==拼接为字符串
	- push（）：在数组的末尾追加元素，并返回新的长度
3. 属性
	- length：数组的长度
5. 特点
	- 数组元素的类型可以是不同的     **eg：** `var arr = [1 , "abc" , true , 变量]`
	- 数组的长度是可以变的   ==与 ArrayList 类似==
### Boolean 
### Date
1. 创建
`var date = new Date();`
3. 方法
	- toLocaleString()：返回当前date 对象对应国家的时间格式
	- getTime()：返回与1970年1月1日零点至今的毫秒值差
### Math
1. 创建
特点：Math对象不用创建，直接使用       **eg：** Math.方法名（）；
2. 方法
- random（）：返回 [ 0 , 1 ) 区间的随机数
- ceil（x）；对数进行向上取整
- floor（x）：对数进行向下取整
- round（x）：把数四舍五入为最接近的整数
3. 属性
PI    **eg：** Math.PI

*** 取1 ~ 100 间的随机整数 
`var number = Math.floor( 100 * Math.random() )`
### Number
### String
### RegExp
[[正则表达式]]是由==普通字符（例如字符 a 到 z）==+==特殊字符（称为"元字符"）==组成的文字模式。
1. 创建
- `var reg = new RegExp("正则表达式");`
- `var reg = /正则表达式/`;
2. 方法
模式串. test（目标串）：验证指定的字符串是否符合正则定义的规范

### Global

1. 特点：全局对象，这个 对象中封装的方法不需要对象就可以直接调用。即：方法名（）;
2. 方法：
编码：
	encodeURL()：url编码
	decodeURL()：url解码
	
	encodeURLComponent()：url编码，编码的字符更多
	decodeURLComponent()：url解码
转换：
	parseInt()：将字符串转为数字
	逐一判断每一个字符是否是数字，==直到==不是数字为止并将==前边数字部分转为number==
判断 ：
	isNaN()：判断一个值是否是Nan
	NaN 六亲不认，连自己都不认（NaN == NaN 值为false）。NaN参与的== 比较全部为false
脚本：
	eval()：将 javaScript 字符串，并把它作为脚本代码来执行
3. URL编码

### Function
1. 创建：
- var 方法名 = new Function（ 形参列表，方法体 ）;
**eg：** `var fun = new Function（ "a" , "b" , “ alert( a+b ) ）;`

- function 方法名（形参列表）{ 方法体 }
**eg：** `function fun1（ a ,b ）{ return（a+b）}`

- var 方法名 = function（形参列表）{ 方法体 }
**eg：** `var fun = function（ a , b ）{ return（ a+b ）}`

2. 方法：
3. 属性：
length：代表形参个数 
4. 特点：
- 方法定义时，形参的类型不用写，返回值类型也不用写
- 方法是一个对象，如果定义名称相同的方法，会覆盖原来的方法
**eg：**
```javaScript
<script>
 var fun = function(){}

func=function(){}
//在此覆盖
</script>
```
- 在js 中， 方法的调用只与方法的名称有关，和参数列表无关。 
	- 在方法声明中 有一个==隐藏==的内置对象（数组）—— arguments,  封装所有的实参
5. 调用
方法名( 实参列表 );

### 自定义对象
格式：
var 对象名称 = {
属性名称1 ： 属性值1 ， 
属性名称2： 属性值 2，
...
函数名称：function（形参列表）{函数体}
...
};

```java
<script>
	var person={
		name : "zhangsan",
		age  : 23,
		address : function(){ alert("北京") }
	};

	alert("person.name");
	alert("person.age");
	person.address();
</script>
```

### BOM对象
##### 介绍
浏览器对象模型：将浏览器的各个组成部分封闭为对象
#### 组成
##### Window
浏览器窗口对象
	获取：直接使用window，其中window，可以省略
	属性：获取其他BOM对象
	方法：
		- alert()：显示警告框
		- confirm()：显示对话框
		- setTimeout()：按照指定的毫秒值来调用函数   ==一次==
	语法：setTimeout（function（）{函数体}   ,  毫秒值）;
		- setInterval()：在指定的毫秒数后调用函数或计算机表达式   ==多次==
	语法：setInterval（ function （）{ 函数体 } , 毫秒值）;
##### Navigator
浏览器对象

##### Screen
屏幕对象

##### History
历史记录对象
1. 方法
forward()：前进
back()：后退
length()：返回窗口访问的网站的个数 
##### Location
地址栏对象
1. 方法
	- reload()：刷新     例 ： `location.reload();`
		`document.getElementByid("btn").onclick=function(){ location.reload };`
	- href()：获取地址栏中的地址  例 ：var url =  location.href();
### DOM对象
>概述：Document Object Model 文档对象模型
>将标记语言的各个组成部分封装为对象
- Document：整个文档对象
- ==Element：元素对象==
	- 获取Element对象
		1. getElementById：通过id 获取对象
		2. getElementsByClassName：根据class属性值获取，返回Element==对象数组==
		3. getElementsByName：根据name属性值 获取，返回Element==对象数组==
		4. getElementsByTagName：根据标签名称获取，返回Element ==对象数组==
	 - 常见 HTML Element 对象的使用
		1. `<div>`标签属性：
			- style（控制样式）
				`对象名.style.color="red";`
			- InnerHTML：设置元素包裹的内容
				`对象名.innterHTML="hello world!"`
		2. 复选框属性：
			- checked：更改状态
				`对象名.checked=true/false`
- Attribute：属性对象
- Text：文本对象
- Comment：注释对象
==依次向下，越来越小，他们之间是父子关系==
当HTML 文档加载到 Web 浏览器中时，它就成了一个==对象== 。文档对象是HTML 文档的根节点
![[file-20240731100720721.png]]


#### 创建其他对象
1. createAttribute(name);创建属性
2. createComment();创建注释
3. createElement();创建元素
4. createTextNode();创建文本节点

3. 
## 事件监听
### 事件绑定
事件绑定有两种方式：
- 方式一：与 html 耦合方式
```javaScript
<input type="button" onclick="on()" />

function on(){ alert("我被点了"); }
```
- 方式二：通过DOM元素属性绑定
```javaScript
<input type="button" id="btn" />

document.getElementByid("btn").onclick=function (){ alert ("我被点了"); }
```
### 常见事件
- onclick：鼠标单击事件
- onblur：元素失去焦点
- onfocus：元素获得焦点
- onload：某个页面或图像已装载
- onsubmit：当表单时触发该事件==有true与false两种值 ，true提交，false不提交
- onkeydown：键盘按下事件
- onmouseover：鼠标移动到某个元素事件
- onmouseout：鼠标移开事件