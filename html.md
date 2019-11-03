# HTML风格指南

## 一. 通用规则

### 1.1 字母大小写

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

### 1.2 末尾空格

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

### 1.3 缩进

整个文件中的缩进应保持前后一致，使用 Tab、2个空格或4个空格都可以，但需保持前后一致。

### 1.4 编码

使用 UTF-8 。

确保你的编辑器将没有字节顺序标记的 UTF-8 用作字符编码。在 HTML 模板中设置编码并用 `<meta charset="utf-8">` 记录。

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

