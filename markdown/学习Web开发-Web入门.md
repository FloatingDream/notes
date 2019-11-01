# 学习 Web 开发 - Web 入门

## Web 概述

* 基础
    > **HTML** (HyeperText Markup Language,超文本标记语言):用于描述、定义页面内容。  
    > **CSS** (Cascading Style Sheets,层叠样式表):用于描述页面内容的外观与展示。  
    > **HTTP** (HyeperText Transfer Protocol,超文本传输协议):用于传输网页中的 HTML 及其他超媒体文档。

* 脚本
    > **JavaScript**:在浏览器中运行的编程语言。它可以为你的网站或应用程序添加交互性和其他动态功能。  
    > **Web API**：Web 应用编程接口用于执行各种任务，例如操作 DOM、播放音频或视频以及生成 3D 图形。  
    > **Web Compoents**：允许你创建可重用的定制元素（它们的功能封装在您的代码之外）并且在您的 Web 应用中使用它们。

* 图形
    > **Canvas**:提供了通过 Javascript 绘制 3D 图形的 API。  
    > **SVG** (Scalable Vector Graphics,可缩放矢量图形):让你能使用线条、曲线和其他几何图形来渲染图形。通过矢量，你可以创建在任意大小能被清晰展现的图像。  
    > **WebGL**:是一种能使用 HTML ```<canvsa>``` 元素来绘制 3D 或 2D 图形的 JavaScript API。它使得你在 Web 内容中能够使用标准 OpenGL ES。

* 其他
    > **WebRTC**: 实时通信，这种技术支持浏览器客户端间的对等视频/音频流和数据共享。  
    > **MathML** (Mathematical Markup Language,数学标记语言)：能显示复杂的数学方法和语法。
    > **XSLT** (Extensible Stylesheet Language Transformations,可扩展样式表语言转换)：能将 XML 文档转换为更易读的 HTML。(EXSLT 扩展了 XSLT 功能)
    > **XPath**:提供了比 CSS 选择器更强大的语法来选择文档中的 DOM 节点。
    > **WebAssembly**:一种可以在现代 Web 浏览器中运行的新型代码。它是一种低级的类汇编语言，具有紧凑的二进制格式、以接近原生的性能运行，并使得 C/C++ 等语言能在 Web 运行。

## HTML 基础

超文本标记语言 (英语：Hypertext Markup Language，简称：HTML ) 是一种用来结构化 Web 网页及其内容的标记语言。网页内容可以是：一组段落、一个重点信息列表、也可以含有图片和数据表。正如标题所示，本文将对 HTML 及其功能做一个基本介绍。

> HTML 不是一门编程语言，而是一种用于定义内容结构的标记语言。HTML 由一系列的元素（elements）组成，这些元素可以用来包围不同部分的内容，使其以某种方式呈现或者工作。

### HTML 元素详解

> 元素的基本部分

![](https://mdn.mozillademos.org/files/16475/element.png)

> 元素的属性:属性包含了关于元素的一些额外信息，这些信息本身不应显现在内容中，主要方便其他操作的时候使用。

![](https://mdn.mozillademos.org/files/16476/attribute.png)

### HTML 文档详解

```html
// <!DOCTYPE html> — 文档类型。混沌初分，HTML 尚在襁褓（大约是 1991/92 年），DOCTYPE 用来链接一些 HTML 编写守则，有点像自动校正等。然而现在已经没有人关心这些，只是因为历史原因必须将它们保留，但没有实际作用。现在你只需要知道这些就可以。
<!DOCTYPE html>
<html> // 这个元素包含了整个页面的内容，有时也被称作根元素。

  <head> // 这个元素放置的内容不是展现给用户的，而是包含例如面向搜索引擎的搜索关键字（keywords）、页面描述、CSS 样式表和字符编码声明等。

    <meta charset="utf-8"> // 这个元素指定了当前文档使用 UTF-8 字符编码 ，UTF-8 包括绝大多数人类已知语言的字符。基本上 UTF-8 可以处理任何文本内容，还可以避免以后出现某些问题，我们没有任何理由再选用其他编码。

    <title>测试页面</title> //这个元素设置页面的标题，显示在浏览器标签页上，同时作为收藏网页的描述文字。

  </head>

  <body> // 这个元素包含期望让用户在访问页面时看到的内容，可以是文本、图像、视频、游戏、可播放的音轨或其他内容。

    <img src="images/firefox-icon.png" alt="测试图片">
  </body>
</html>
```

## CSS 基础

> 层叠样式表（Cascading Style Sheet，简称：CSS）是为网页添加样式的代码。和 HTML 类似，CSS 也不是真正的编程语言，甚至不是标记语言。它是一门样式表语言，这也就是说人们可以用它来选择性地为 HTML 元素添加样式。

### CSS 规则集

![](https://mdn.mozillademos.org/files/16483/css-declaration.png)

* **选择器**（Selector）:HTML 元素的名称位于规则集开始。它选择了一个或多个需要添加样式的元素（在这个例子中就是 p 元素）。要给不同元素添加样式只需要更改选择器就行了。
* **声明**（Declaration）:一个单独的规则。如 color: red; 用来指定添加样式元素的属性。
* **属性**（Properties）:改变 HTML 元素样式的途径。
* **属性的值**（Property value）:在属性的右边，冒号后面即属性的值，它从指定属性的众多外观中选择一个值。

### 不同类型的选择器

常用类选择器

选择器名称 | 选择的内容 | 示例
---|---|---
元素选择器 | 所有指定类型的 HTML 元素 | ```p```<br/>选择```<p>```
ID 选择器 | 具有特定 ID 的元素 | ```#my-id```<br/>选择```<p id="my-id"></p>```
类选择器 | 具有特定类的元素 | ```.my-class```<br/>选择```<p class="my-class"></p>```
属性选择器 | 拥有特定属性的元素 | ```img[src]```<br/>选择```<img src="myimage.png">```
伪类选择器 | 特定状态下的特定元素 | ```a:hover```<br/>仅在鼠标悬浮在链接的时候选择

### 盒子模型

使用 CSS 设置尺寸、颜色、位置等等，都类似围绕一个一个盒子展开的,CSS 布局主要就是基于盒模型的。
> every element in web design is a rectangular box.

![](https://mdn.mozillademos.org/files/9443/box-model.png)

每个占据页面空间的元素都有这些属性：

* **padding**:即内边距，围绕着内容（比如段落）的空间。
* **border**：即边框，紧接着内边距的线。
* **margin**：即外边距，围绕元素外部的空间。

## Javascript 基础

> JavaScript（缩写：JS）是一门完备的 动态编程语言。当应用于 HTML 文档时，可为网站提供动态交互特性。由布兰登·艾克（ Brendan Eich，Mozilla 项目、Mozilla 基金会和 Mozilla 公司的联合创始人）发明。

### 变量(Variable)

> 变量是存储值的容器。

```js
// 定义后赋值
let myVariable;
myVariable = '李雷';
// 定义与赋值写在一行
let myVariable = '李雷';
// 通过变量名取得变量的值
myVariable;
// 变量赋值后更改
let myVariable = '李雷';
myVariable = '韩梅梅';
```

> 变量的数据类型

变量 | 解释 | 示例
---|---|---
String | 字符串（一串文本）。字符串的值必须将用引号（单双均可，必须成对）扩起来。 | ```let myVariable = '李雷';```
Number | 数字，基于 IEEE 754 标准的双精度 64 位二进制格式的值（-(263 -1) 到 263 -1）。 | ```let myVariable = 10;```
BigInt | 整数，可以用任意精度表示整数。 | ```const x = 2n ** 53n;```
Boolean | 布尔值（真 / 假）。 true/false 是 JS 里的特殊关键字，无需引号。 | ```let myVariable = true;```
Symbol | 符号,是ECMAScript 第6版新定义的。符号类型是唯一的并且是不可修改的。 | ```var  myPrivateMethod  = Symbol();this[myPrivateMethod] = function() {...};```
Null | 值 null 特指对象的值未设置 | ```let myVariable = null```
Undefined | 一个没有被赋值的变量会有个默认值 undefined
Object | 对象，JavaScript 里一切皆对象，一切皆可储存在变量里。这一点要牢记于心。 | ```let myVariable = document.querySelector('h1');```

> 前7种是原始类型后面一种是对象，一共8种类型。

### 运算符

> 运算符 是一类数学符号，可以根据几个值（或变量）产生结果。例如：```+;-;*;/;=;===;!==;!;等等```

### 条件语句

> 条件语句是一种代码结构，用来测试表达式的真假，并根据测试结果运行不同的代码。例如：```if...else```

### 函数

> 函数 用来封装可复用的功能。如果没有函数，一段特定的操作过程用几次就要重复写几次，而使用函数则只需写下函数名和一些简短的信息。

```js
let myVariable = document.querySelector('h1');
alert('hello!');
```

 ```document.querySelector;alert``` 是浏览器内置的函数。

自定义函数：

```js
function multiply(num1, num2) {
  let result = num1 * num2;
  return result;
}

multiply(4, 7);
multiply(20, 20);
multiply(0.5, 3);
```

### 事件

> 事件能为网页添加真实的交互能力。它可以捕捉浏览器操作并运行一些代码做为响应。最简单的事件是 点击事件(```onclick```)，鼠标的点击操作会触发该事件。

## 当你在浏览器里输入一个网址,敲击回车发生了什么

1. 浏览器在域名系统服务器上找出存放网页的服务器的实际地址（找出商店的位置）。- DNS 查询
2. 浏览器发送 HTTP 请求信息到服务器来请拷贝一份网页到客户端（你走到商店并下订单）。这条消息，包括其他所有在客户端和服务器之间传递的数据都是通过互联网使用 TCP/IP 协议传输的。- 数据请求
3. 服务器同意客户端的请求后，会返回一个“200 OK”信息，意味着“你可以查看这个网页，给你～”，然后开始将网页的文件以数据包的形式传输到浏览器（商店给你商品，你将商品带回家）。- 数据回传
4. 浏览器将数据包聚集成完整的网页然后将网页呈现给你（商品到了你的门口 —— 新东西，好棒！）。- 解析数据
