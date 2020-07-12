---
html:
  embed_local_images: false
  embed_svg: true
  offline: false
  toc: true

print_background: false
---

# HTML 风格指南

## 一. 通用规则

### 1.1 编码

使用 UTF-8 。

确保你的编辑器将没有字节顺序标记的 UTF-8 用作字符编码。在 HTML 模板中设置编码并用 `<meta charset="utf-8">` 记录。

### 1.2 字母大小写

仅使用小写。

所有代码均使用小写，该规则适用于 HTML 元素名、属性和属性值（文本/ CDATA 除外）。

**不推荐：**

```html
<A HREF="/" class="HOME">主页</A>
```

**推荐：**

```html
<a href="/" class="home">主页</a>
```

### 1.3 末尾空格

删除行尾空格。

行尾空格属于多余的符号，并且会让 diff 变得更加复杂。

**不推荐：**

```html
<p>什么?</p>__
```

**推荐：**

```html
<p>一往情深深几许？深山夕照深秋雨。</p>
```

如果你使用 VS Code，你可进入编辑器菜单的「首选项——>设置」中搜索 `files.trimTrailingWhitespace` ，然后将选项勾选即可，这样每当你保存文件时，去除行尾空格操作便会自动完成：

```json
"files.trimTrailingWhitespace": true
```

### 1.4 缩进

整个文件中的缩进应保持前后一致，使用 Tab、2个空格或4个空格都可以，但需保持前后一致。

### 1.5 注释

在可行和必要时，对代码进行注释。

用注释解释代码的覆盖范围、目的和作用以及使用和选择各解决方案的原因。

### 1.6 待办任务

用 `TODO:` 标注待办事项和任务项

仅用关键词 `TODO` 标注待办事项，不要使用 `@@` 等其他格式的字样。在任务项前加冒号，如： `TODO: 待办任务`

**推荐：**

```html
<!-- TODO: 对出下联 -->
<ul>
   <li>风吹云，云随风，风云变幻</li>
</ul>
```

## 二. HTML 样式规则

### 2.1 文件类型

使用 HTML5 。

所有 HTML 文件均应使用 HTML5 （ HTML 语法）： `<!DOCTYPE html>`

不要结束自结束元素，即编写 `<br>` ，而不是 `<br /> `。

### 2.2 语义

根据目的使用 HTML 。

根据元素的预期作用使用元素。例如，针对标题使用标题元素，针对段落使用 p 元素，针对锚点使用 a 元素等。根据目的使用 HTML 对提高可访问性、再利用程度和代码效率十分重要。

**不推荐：**

```html
<div onclick="goToRecommendations();">All recommendations</div>
```

**推荐：**

```html
<a href="recommendations/">All recommendations</a>
```

### 2.3 多媒体应变计划

为多媒体设置备用内容。

确保为图片、视频或通过画布呈现的动画对象等多媒体提供其他访问方式。对于图片而言，使用有意义的 Alt 文本。对于视频，使用音频转述资料和字幕（如有）。

为方便访问，需提供备用内容，若没有 `alt` 属性，盲人用户将难以辨别图片的内容，其他用户也可能无法理解视频或音频的内容。

针对具有会引入冗余的 `alt` 属性的图片和无法立即使用 CSS 的装饰性图片，使用空备用内容，即 `alt=""` 。

**不推荐：**

```html
<img src="udacity.png">
```

**推荐：**

```html
<img src="udacity.png" alt="Udacity logo">
```

### 2.4 关注点分离

将结构、描述和行为相互分离。

将结构（标记）、描述（样式）和行为（脚本设计）严格分开，将三者间可能发生的相互作用降至最低。

也就是说，确保文件和模板仅含有 只用于结构目的 HTML 。将所有描述性事物移至样式表，将所有行为性事物移至脚本。此外，尽可能少地连接文件和模板中的样式表和脚本，以便使接触面积最小化。

将结构、描述和行为相互分离对维护十分重要。相比对样式表和脚本进行更新，更改 HTML 文件和模板的成本往往更高。

**不推荐：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
   <style>
   /*
      此处省略 n 行样式
   */
   </style>
</head>
<body>
   <script>
   // 此处省略 n 行脚本
   </script>
</body>
</html>
```

**推荐：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Document</title>
   <link rel="stylesheet" href="style.css">
</head>
<body>
   <script src="js/app.js"></script>
</body>
</html>
```

### 2.5 类型属性

忽略样式表和脚本的 type 属性。

不要针对样式表和脚本使用 type 属性。因为 HTML 已经默认设置了 `text/css` 和 `text/javascript` ，所以在此类语境中无需设置 type 属性。

在老式浏览器中，也可以安全进行此项操作。

**不推荐：**

```html
<link rel="stylesheet" type="text/css" href="css/style.css">
<script src="js/app.js" type="text/javascript"></script>
```

**推荐：**

```html
<link rel="stylesheet" href="css/style.css">
<script src="js/app.js"></script>
```

## 三. HTML 格式规则

### 3.1 一般格式

所有代码块、列表和表元素均需另起一行，所有子元素均需缩进。

每一个代码块、列表和表元素均需另起一行，与元素的样式相独立（因为 CSS 允许元素在每一个显示属性中担任不同的角色）。

此外，代码块、列表和表元素的子元素也需进行缩进（如果你遇到列表项间存在空白的问题，可以将所有 `li` 元素放置在一行）。

**推荐:**

```html
<blockquote>
   <p>啊！<em>船长！</em>我的船长！</p>
</blockquote>
<ul>
   <li>啊．船长，我的船长！我们艰苦的航程已经终结，</li>
   <li>这只船安然渡过了一切风浪，我们寻求的奖赏已经获得。</li>
   <li>港口在望，我听见钟声在响，人们都在欢呼，</li>
   <li>目迎着我们的船从容返航，它显得威严而英武。</li>
   <li>可是，啊，心啊！心啊！心啊！</li>
   <li>啊．殷红的鲜血长流，</li>
   <li>在甲板上，那里躺着我的船长，</li>
   <li>他已倒下，已死去，已冷却。</li>
   <li>啊，船长，我的船长！起来吧，起来听听这钟声，</li>
   <li>起来，——旌旗正为你招展——军号正为你发出颤音。</li>
   <li>为你．送来了这些花束和花环。</li>
   <li>为你，熙攘的群众在呼唤，转动着多少殷切的脸。</li>
   <li>这里，船长！亲爱的父亲！</li>
   <li>你头颅下边是我的手臂！</li>
   <li>在甲板上像是在一场梦里，</li>
   <li>你已倒下，已死去，已冷却。</li>
   <li>我们的船长不作回答，他的双唇惨白而寂静，</li>
   <li>我的父亲不能感觉我的手臂，他已没有脉息、没有知觉，</li>
   <li>我们的船已安全抛锚碇泊，已经结束了它的航程，</li>
   <li>胜利的船从险恶的旅途归来，我们寻求的已赢得手中。</li>
   <li>欢呼吧，啊，海岸！轰鸣，啊，洪钟！</li>
   <li>可是，我却轻移悲伤的步履，</li>
   <li>在甲板上，那里躺着我的船长，</li>
   <li>他已倒下，已死去，已冷却。</li>
</ul>
<table>
   <thead>
      <tr>
         <th scope="col">姓名</th>
         <th scope="col">职业</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>瓦尔特·惠特曼</td>
         <td>诗人</td>
      </tr>
   </tbody>
</table>
```

### 3.2 HTML 引号

在引用属性值时，使用双引号。

**不推荐：**

```html
<a href='login/' class='btn btn-secondary'>登录</a>
```

**推荐：**

```html
<a href="login/" class="btn btn-secondary">登录</a>
```

# CSS 风格指南

## 一. 通用规则

### 1.1 编码

使用 UTF-8 。

确保你的编辑器将没有字节顺序标记的 UTF-8 用作字符编码。

### 1.2 字母大小写

仅使用小写。

所有代码均使用小写，该规则适用于 CSS 选择符、属性和属性值（字符串除外）。

**不推荐：**

```css
color: #E5E5E5;
```

**推荐：**

```css
color: #e5e5e5;
```

### 1.3 末尾空格

删除行尾空格。

行尾空格属于多余的符号，并且会让 diff 变得更加复杂。

**不推荐：**

```css
border: 0;__
```

**推荐：**

```css
border: 0;
```

如果你使用 VS Code，你可进入编辑器菜单的「首选项——>设置」中搜索 `files.trimTrailingWhitespace` ，然后将选项勾选即可，这样每当你保存文件时，去除行尾空格操作便会自动完成：

```json
"files.trimTrailingWhitespace": true
```

### 1.4 缩进

整个文件中的缩进应保持前后一致，使用 Tab、2个空格或4个空格都可以，但需保持前后一致。

### 1.5 注释

在可行和必要时，对代码添加注释。

用注释解释代码的覆盖范围、目的和作用以及使用和选择各解决方案的原因。

### 1.6 区块注释

在可行时，用注释将样式表区块组合在一起，用新行分隔各区块。

**推荐：**

```css
/* Header */
.header {
   …
}

.header-nav {
   …
}

/* Content */
.gallery {
   …
}

.gallery-img {
   …
}

/* Footer */
.footer {
   …
}

.footer-nav {
   …
}
```

### 1.7 待办任务

用 `TODO:` 标注待办事项和任务项：

仅用关键词 `TODO` 标注待办事项，不要使用 `@@` 等其他格式的字样。在任务项前加冒号，如：`TODO: 待办任务` 。

**推荐：**

```css
/* TODO: 添加一个按钮元素 */
```

## 二. CSS 样式规则

### 2.1 ID 和 CLASS 名称

使用有意义或具有普遍性的 ID 和类名称。

不可使用意义含糊的 ID 和类名称，使用能够反映相应元素意义的名称或具有普遍性的通用名。

最好使用能够反映相应元素意义的具体名称，因为这些名称最易于理解且不易变更。

具有普遍性的通用名被用于与类似元素意义相仿的元素，主要起辅助作用。

**不推荐：**

```css
.p-998 {
   …
}

.btn-green {
   …
}
```

推荐：

```css
.gallery {
   …
}

.btn-default {
   …
}
```

### 2.2 类型选择符

避免用类型选择器限定 ID 和类名称。

除非情况需要（例如，在辅助类型中），否则不要将元素名和 ID 或类名称同时使用。为提高性能，避免使用不必要的祖先选择符。

在 CSS 文件中使用 ID 也是较糟糕的做法，类别始终比名称更具优势，如果你需要给予某元素一个特殊的名称，请使用类别。（ ID 的唯一优点是在存在数千个类似元素的页面上能保持较快的运行速度。）

**不推荐：**

```css
ul#example {
   …
}

div.error {
   …
}
```

**推荐：**

```css
.example {
   …
}

.error {
   …
}
```

### 2.3 简写属性

应使用简写。

CSS 可提供多种简写属性（例如，padding，而不是 padding-top、padding-bottom 等），应尽可能使用这些简写，但字体属性和在 Bootstrap 等框架中会覆盖其他同名属性的属性除外。

使用简写属性有助于提高代码的效率和易懂性。推荐在设置仅与字体 font 相关的属性时使用字体简写属性，但无需在进行小幅改动时使用。在使用字体简写属性时，请注意，如果未注明字体的大小和系列，浏览器会忽略整个字体声明。

不推荐：

```css
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;
```

**推荐：**

```css
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```

### 2.4 省略0后面的单位

去掉 `0` 值后面的单位。

**不推荐：**

```css
margin: 0em;
padding: 0px;
```

**推荐：**

```css
margin: 0;
padding: 0;
```

### 2.5 前导零

为方便阅读，十进制值中含有前导零。

**不推荐：**

```css
font-size: .8em;
```

**推荐：**

```css
font-size: 0.8em;
```

### 2.6 十六进制表示法

在可行时，使用三个十六进制表示法的字符。

**不推荐：**

```css
color: #eebbcc;
```

**推荐：**

```css
color: #ebc;
```

### 2.7 ID 和 CLASS 名称分隔符

用连字符分隔 ID 和类名称中的字词 `-`。

用连字符连接选择符中的词语和缩略词，以方便理解和扫描。

唯一的例外：在编写 [BEM](http://getbem.com/naming/) 样式 CSS 选择符时也可以使用下划线 `_` 。

**不推荐：**

```css
.demoimage {
   …
}

.errorStatus {
   …
}
```

**推荐：**

```css
.demo-image {
   …
}

.error-status {
   …
}
```

### 2.8 Hack

避免用户代理检测或 CSS Hack ——尝试另一种方法。

人们可能很想处理用户代理检测或特殊的 CSS 过滤器以及应变方案和非法入侵之间的样式差异。这两项措施均为实现和维护有效和可处理的代码库的最后方案。请考虑该样式是否对应用的性能至关重要，需要该样式的用户代理是否可以不采样该样式。

## 三. CSS 格式规则

### 3.1 代码块内容缩进

缩进所有代码块内容，即规则内的规则和声明，以反映层次结构、方便理解。

推荐：

```css
@media screen, projection {
   html {
      background: #fff;
      color: #444;
   }
}
```

### 3.2 声明标点

在所有声明后使用分号，以增加连贯性和延展性。

**不推荐：**

```css
.test {
   display: block;
   height: 100px
}
```

**推荐：**

```css
.test {
   display: block;
   height: 100px;
}
```

### 3.3 属性名标点

所有属性名冒号后均需添加空格，但属性和冒号间不加空格，以增加连贯性。

**不推荐：**

```css
font-weight:bold;
padding : 0;
margin :0;
```

**推荐：**

```css
font-weight: bold;
padding: 0;
margin: 0;
```

### 3.4 声明区标点

最后一个选择符和声明区起始处的左大括号之间需加空格。

**不推荐：**

```css
.video-block{
   margin: 0;
}

.audio-block{
   margin: 0;
}
```

**推荐：**

```css
.video-block {
   margin: 0;
}

.audio-block {
   margin: 0;
}
```

### 3.5 选择符和声明分隔

所有选择符和声明均需另起一行。

**不推荐：**

```css
h1, h2, h3 {
   font-weight: normal;
   line-height: 1.2;
}
```

**推荐：**

```css
h1,
h2,
h3 {
   font-weight: normal;
   line-height: 1.2;
}
```

### 3.6 规则分隔

所有规则间均需加一个空行（两个换行符）。

**推荐：**

```css
html {
   background: #fff;
}

body {
   margin: auto;
   width: 50%;
}
```

### 3.7 CSS 引号

属性选择符和属性值均需使用双引号，链接值 `url()` 中不可使用双引号。

**不推荐：**

```css
@import url("css/links.css");
html {
   font-family: 'Open Sans', arial, sans-serif;
}
```

**推荐：**

```css
@import url(css/links.css);
html {
   font-family: "Open Sans", arial, sans-serif;
}
```

# JavaScript 风格指南

## 一. 通用规则

### 1.1 编码

使用 UTF-8（无 BOM）。

确保你的编辑器将没有字节顺序标记的 UTF-8 用作字符编码。

### 1.2 末尾空白

删除行尾空格。

行尾空格属于多余的符号，并且会让 diff 变得更加复杂。

**不推荐：**

```javascript
const name = "John Smith";__
```

**推荐：**

```javascript
const name = "John Smith";
```

如果你使用 VS Code，你可进入编辑器菜单的「首选项——>设置」中搜索 `files.trimTrailingWhitespace` ，然后将选项勾选即可，这样每当你保存文件时，去除行尾空格操作便会自动完成：

```json
"files.trimTrailingWhitespace": true
```

### 1.3 缩进

整个文件中的缩进应保持前后一致，使用 Tab、2个空格或4个空格都可以，但需保持前后一致。

### 1.4 注释

用注释解释代码的覆盖范围、目的和作用以及使用和选择各解决方案的原因。

你可以选择使用 [JSDoc](http://usejsdoc.org/)，即编写代码注释的文件生成器和标准，对你的 JavaScript 功能进行记录，其优点包括为你的注释提供技术参照和能够针对文件生成网页的命令行 jsdoc 工具。 JSDoc 会为你提供记录代码的多种注释，但我们只推荐你使用以下种类：

- [@constructor](http://usejsdoc.org/tags-class.html)：用于记录一个 Class 类，也就是用 `new` 关键字调用的函数。
- [@description](http://usejsdoc.org/tags-description.html)：用于描述你的函数，该标签还可以使你在需要时添加 HTML 标记。
- [@param](http://usejsdoc.org/tags-param.html)：用于描述函数参数的名称、类别和说明。
- [@returns](http://usejsdoc.org/tags-returns.html)：记录函数返回值的类型和说明。

下方实例说明了如何记录类构造函数（注意注释区开头使用的 `/**` ，这个非常重要）：

```javascript
/**
* @description 简要描述这本书
* @constructor
* @param {string} title - 书的标题
* @param {string} author - 书的作者
*/

function Book(title, author) {
   ...
}
```

以下函数含有能返回值的参数，注意，这里的参数作用一目了然，因此并未对其进行说明。

```javascript
/**
* @description 计算两数相加
* @param {number} a
* @param {number} b
* @returns {number} 数字 a 与 b 的和
*/

function sum(a, b) {
   return a + b;
}
```

你也可以使用更多你想要编写的注释。

### 1.5 待办任务

用 `TODO:` 标注待办事项和任务项

仅用关键词 `TODO` 标注待办事项，不要使用 `@@` 等其他格式的字样。在任务项前加冒号，如： `TODO: 待办任务`

**推荐：**

```javascript
// TODO: 加些其他的需求
```

## 二. JavaScript 语言规则

### 2.1 变量

在 JavaScript 里一共有三种定义变量的方式：

- [const](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const)
- [let](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let)
- [var](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/var)

当定义变量的时候，你应该使用上面列出的关键字来定义变量。优先考虑使用 `const` 定义你的变量，如果觉得以后需要对变量重新赋值的，则使用 `let`。现在已经不推荐使用 `var` 关键字来定义变量了。

### 2.2 分号

始终使用分号。

依靠隐式插入会造成难以排除的细微问题。分号应放在**函数表达式**的末尾，而不是**函数声明**的末尾。

**不推荐：**

```javascript
const foo = function() {
   return true // 缺少分号
} // 缺少分号
function foo() {
   return true;
}; // 额外的分号
```

**推荐：**

```javascript
const foo = function() {
   return true;
};
function foo() {
   return true;
}
```

### 2.3 基本类型包装对象

基本类型无需使用包装对象，此外，包装对象还具有潜在危险，但可以使用类型转换。

**不推荐：**

```javascript
const x = new Boolean(0);
if (x) {
   alert('hi');	// 如果 x 是一个真实对象，则显示 hi
}
```

**推荐：**

```javascript
const x = Boolean(false);
if (x) {
   alert('hi');	// 如果 x 是一个否定的布尔值，则显示 hi
}
```

### 2.4 闭包

进行该操作时要小心谨慎。 创建闭包的能力可能是 JavaScript 中最有用但最常被忽略的能力。需要记住的是，闭包会储存对其封闭范围的指针，因此，将 DOM 元素与闭包相连会生成循环引用，从而导致内存的泄露。

**不推荐：**

```javascript
function foo(element, a, b) {
   element.onclick = function() { /* 使用 a 和 b */ }
}
```

**推荐：**

```javascript
function foo(element, a, b) {
   element.onclick = bar(a, b);
}
function bar(a, b) {
   return function() { /* 使用 a 和 b */ }
}
```

### 2.5 for 、for-in 和 forEach

#### for循环

使用 for 循环过程中，数组的长度，使用一个变量来接收，这样有利于代码执行效率得到提高，而不是每走一次循环，都得重新计算数组长度

**不推荐：**

```js
for(let i = 0; i < arr.length, i++){}
```

**推荐：**

```js
for(let i = 0, len = arr.length; i<len; i++){}
```

#### 数组

在迭代数组时，相比 `for-in` 循环， `forEach` 或 `for` 循环更具优势。

**不推荐：**

```javascript
const myArray = ['a', 1, 'etc'];
for (const indexNum in myArray) {
   console.log(myArray[indexNum]);
}
const starWars = {
   "creatures": [
      {
         "name": "bantha",
         "face": "furry"
      },
      {
         "name": "loth-cat",
         "face": "toothy"
      }
   ]
};
for (const i in starWars.creatures) {
   console.log(starWars.creatures[i].name);
   console.log(starWars.creatures[i].face);
};
```

**推荐：**

```javascript
const mySimpleArray = ['a', 1, 'etc'];
const mySimpleArray.forEach(function(val) {
   console.log(val);
});
const starWars = {
   "creatures": [
      {
         "name": "bantha",
         "face": "furry"
      },
      {
         "name": "loth-cat",
         "face": "toothy"
      }
   ]
};
starWars.creatures.forEach(function(creature){
   console.log(creature.name);
   console.log(creature.face)
});
// 或者
const myArray = ['a', 1, 'etc'];
for (let indexCount = 0; indexCount < myArray.length; indexCount++) {
   console.log(myArray[indexCount]);
};
```

#### 对象

`for-in` 循环用于在对象中循环关键词。这样很容易出错，因为， `for-in` 不会从 `0` 循环，而是循环对象及其原型链中现存的所有关键词。 如果可以的话，对数据进行整理，以避免迭代对象。如果不可行，将 `for-in` 循环的内容包裹在条件语句中，以避免迭代原型链。

`for-in` 循环用于循环对象中的键。这很容易出错，因为 `for-in` 不是从 `0` 循环到 `length-1` ，而是循环对象及其**原型链**中的所有现有键。

如果可以的话，对数据进行整理，这样就不必在对象上迭代。如果不可行，就将 `for-in` 循环的内容包裹在条件语句中，以防止它在原型链上迭代。

**不推荐：**

```javascript
const myObj = {'firstName':'Ada','secondName':'Lovelace'};
for (const key in myObj) {
   console.log(myObj[key]);
}
```

**推荐：**

```javascript
const myObj = {'firstName':'Ada','lastName':'Lovelace'};
for (const key in myObj) {
   if (myObj.hasOwnProperty(key)) {
      console.log(myObj[key]);
   }
}
```

### 2.6 多行字符串字面量

不要使用。 编译期间无法妥善删除各行开头的空格，斜杠后的空白会引发棘手的问题，虽然大部分脚本引擎支持该操作，但这并不属于规格中的一部分。

**不推荐：**

```javascript
const myPoetry = '一二三四五，\
   上山打老虎，\
   老虎没打到，\
   打到小松鼠，\
   让我数一数，\
   一二三四五';
```

**推荐：**

```javascript
const myPoetry = '黄河远上白云间，' +
   '一片孤城万仞山。' +
   '羌笛何须怨杨柳，' +
   '春风不度玉门关。';

// or
const myPoetry = `
   黄河远上白云间，
   一片孤城万仞山。
   羌笛何须怨杨柳，
   春风不度玉门关。
`;
```

### 2.7 数组和对象字面量

使用数组和对象字面量，而不是数组和对象构造函数。

**不推荐：**

```javascript
const myArray = new Array(x1, x2, x3);
const myObject = new Object();
myObject.a = 0;
```

**推荐：**

```javascript
const myArray = [x1, x2, x3];
const myObject = {
   a: 0
};
```

## 三. JavaScript 样式规则

### 3.1 命名

总体来说，函数名称为 `functionNames` ，变量名称为 `variableNames` ，类名称为 `ClassNames` ，方法名称为 `methodNames` ，常量值名称为 `CONSTANT_VALUES` ，文件名称为 `filenames` 。

### 3.2 代码格式

由于分号的隐式插入，大括号应与其内容放置在同一行。

**推荐：**

```javascript
if (something) {
   // 执行某项任务
} else {
   // 执行另外一项任务
}
```

只有在单行数组和对象初始器可以在写同一行时方可使用这两项。左括号前和右括号后都不应有空格。

**推荐：**

```javascript
const array = [1, 2, 3];
const object = {a: 1, b: 2, c: 3};
```

多行数组和对象初始器需进行单行缩进，与代码块一样，其括号与内容应位于同一行。

**推荐：**

```javascript
const array = [
   'Joe <joe@email.com>',
   'Sal <sal@email.com>',
   'Murr <murr@email.com>',
   'Q <q@email.com>'
];

const object = {
   id: 'foo',
   class: 'foo-important',
   name: 'notification'
};
```

### 3.3 字符串

为了保持连贯性，应使用单引号 `'` 而不是双引号 `"`。这在创建含有 HTML 的字符串时尤其有帮助。

**推荐：**

```javascript
const element = 'Click Me';
```

此规则较为明显的一个例外是在 JSON 对象中： **JSON 要求使用双引号**。

## 四. 技巧提示

### 4.1 真假布尔表达式

以下为**假**的布尔表达式：

- `null`
- `undefined`
- `''` 空字符串
- 数字 `0`

注意区分，以下为**真**的表达式：

- `'0'` 字符串0
- `[]` 空数组
- `{}` 空对象

### 4.2 三元表达式 `expr ? A : B`

不强制规定，但建议使用三元条件运算符编写简洁代码，避免使用以下代码：

**不推荐：**

```javascript
if (val) {
   return foo();
} else {
   return bar();
}
```

**推荐：**

```javascript
return val ? foo() : bar();
```

### 4.3 短路求值 `&&` 和 `||`

短路求值是一种逻辑运算符的求值策略。只有当第一个运算数的值无法确定逻辑运算的结果时，才对第二个运算数进行求值。例如，当 `&&` 的第一个运算数的值为 `false` 时，其结果必定为 `false` ；当 `||` 的第一个运算数为 `true` 时，最后结果必定为 `true` ，在这种情况下，就不需要知道第二个运算数的具体值。

**不推荐：**

```javascript
function foo(name) {
   let theName;
   if (name) {
      theName = name;
   } else {
      theName = 'John';
   }
   return theName;
}
```

**推荐：**

```javascript
function foo(name) {
   return theName = name || 'John';
}
```

#### 4.4 && 也被用于缩减代码

**不推荐：**

```javascript
if (node) {
   if (node.kids) {
      console.log(node.kids);
   }
}
```

**推荐：**

```javascript
if (node && node.kids) {
   console.log(node.kids);
}
```

##### 4.5 使用拓展运算符做数组浅拷贝

**不推荐：**

```js
let arr = [1, 2, 3]
const len = arr.length
const copyArr = []

for (let i = 0; i < len; i += 1) {
  copyArr[i] = arr[i]
}

// or

copyArr = [].concat(arr);
```

**推荐：**

```js
const copyArr = [...arr]
```

#### 4.6 使用拓展运算符做对象浅拷贝

**不推荐：**

```js
const original = { a: 1, b: 2 }
const copy = Object.assign(original, { c: 3 })
delete copy.a //  改变了 original

const original = { a: 1, b: 2 }
const copy = Object.assign({}, original, { c: 3 }) // copy => { a: 1, b: 2, c: 3 }
```

**推荐：**

```js
const original = { a: 1, b: 2 }
const copy = { ...original, c: 3 } // copy => { a: 1, b: 2, c: 3 }
```

# Git 风格指南

## 提交信息

### 信息结构

提交信息由空行分隔的三个不同部分组成：`标题`、`正文`（可选）和`页脚`（可选）。布局如下：

```shell
type: subject

body

footer
```

标题由信息类型和标题组成。

### 类型

类型包含在标题中，可以是这些类型之一:

- **feat:** 新功能（feature）
- **fix:** 修复bug
- **docs:** 文档
- **style:** 格式（不影响代码运行的变动）e.g. 分号缺失，统一缩进
- **refactor:** 重构（即不是新增功能，也不是修改bug的代码变动）
- **test:** 添加测试
- **chore:** 构建任务，包管理器配置或辅助工具的变动

### 主题

commit 目的的简短描述，最好不超过50个字符，结尾不加句号。

### 正文

对本次 commit 的详细描述。用来解释提交的内容和原因。

正文是可选部分，因为并不是所有提交都复杂到需要正文来详细描述。

写正文时，标题和正文之间必须有空白行，每行的长度不能超过72个字符。

### 页脚

页脚是可选的，用来记录当前 commit 针对的是哪个 issue。

### 示例

```shell
feat: 50个字符以内的简短描述

如过有必要，可以在正文部分添加更详细的说明文本。字数大约为72个字符。写正文时，标题和正文之间必须有空白行；如果同时运行 `log`、`shortlog` 和 `rebase` 等工具，可能会混淆。

解释此提交要解决的问题。重点关注为什么要进行此更改，而不是如何进行更改(代码对此进行了解释)。这种变化是否有副作用或其他不直观的结果？在这里解释一下。


如果想要记录当前 commit 针对的是哪个issue，可以这样编写：

Resolves: #123
```
