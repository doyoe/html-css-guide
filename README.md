# HTML/CSS开发规范指南

## 目录

1. [规范概述](#intro)
2. [基本信息](#profile)
3. [通用约定](#general)
4. [HTML约定](#html)
5. [CSS约定](#css)

<a name="intro"></a>
## 规范概述

规范的制定是我们长期以来对工作的积累与沉淀的产物，帮助我们更快、更好、更高效的完成繁重、复杂、多样化的任务，我们制作规范的主要目的在于：

* 降低每个组员介入项目的门槛成本；
* 提高工作效率及协同开发的便捷性；
* 高度统一的代码风格；
* 提供一整套HTML、CSS解决方案，来帮助开发人员快速做出高质量的符合要求的页面；

<a name="profile"></a>
## 基本信息

规范名称 | Cook
--------|------|
当前版本 | v0.0.1
规范制定 | 杜瑶 and you?
最后更新 | 2014.08.29

<a name="general"></a>
## 通用约定

### 1.文档目录结构

待添加。。。

### 2.分离

结构（HTML）、表现（CSS）、行为分离（JavaScript）

> 将结构与表现、行为分离，保证它们之间的最小耦合，这对前期开发和后期维护都至关重要。

### 3.缩进

使用tab（4个空格宽度）来进行缩进，可以在IDE里进行设置

### 4.编码

* 以 UTF-8 无 BOM 编码作为文件格式；
* 在HTML中文档中用 `<meta charset="utf-8" />` 来指定编码；
* 不需要为CSS显示定义编码，因为它默认为utf-8；

### 5.小写

* 所有的HTML标签必须小写
* 所有的HTML属性必须小写
* 所有的样式名及规则必须小写

### 6.注释

尽可能的为你的代码写上注释。解释为什么要这样写，它是新鲜的方案还是解决了什么问题。

### 7.待办事项

用 TODO 标示待办事项和正在开发的条目

	<!-- TODO: 图文混排 -->
	<div class="g-imgtext">
	<img src="1.png" alt="" />
	...

	/* TODO: 图文混排 comm: g-imgtext */
	.g-imgtext{...}

### 8.行尾空格

删除行尾空格，这些空格没有必要存在

### 9.省略嵌入式资源协议头

省略图像、媒体文件、样式表和脚本等URL协议头部声明 ( http: , https: )。如果不是这两个声明的URL则不省略。

省略协议声明，使URL成相对地址，防止内容混淆问题和导致小文件重复下载（这个主要是指http和https交杂的场景中）。

不推荐：

	<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

推荐：

	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
	
不推荐：

```
.example {
  background: url(http://www.google.com/images/example);
}
```

推荐：

```
.example {
  background: url(//www.google.com/images/example);
}
```

> 注：省略协议头在IE7-8下会有一点小问题，外部CSS文件（link和@import）会被下载两遍，所以该条目的约定看具体项目。

### 10.代码有效性

* 使用 [W3C HTML Validator](http://validator.w3.org/) 来验证你的HTML代码有效性；
* 使用 [W3C CSS Validator](http://jigsaw.w3.org/css-validator/) 来验证你的CSS代码有效性；

> 代码验证不是最终目的，真的目的在于让开发者在经过多次的这种验证过程后，能够深刻理解到怎样的语法或写法是非标准和不推荐的，即使在某些场景下被迫要使用非标准写法，也可以做到心中有数。

<a name="html"></a>
## HTML约定

### 1.文档类型

* 统一使用HTML5的标准文档类型：`<!DOCTYPE html>`

> HTML5文档类型具备前后兼容的特质，并且易记易书写

* 在文档doctype申明之前，不允许加上任何非空字符

> 任何出现在doctype申明之前的字符都将使得你的HTML文档进入非标准模式

* 不允许添加<meta>属性强制改变文档模式

> 避免出现不可控的问题

### 2.省略type属性

在调用CSS和JavaScript时，可以将type属性省略不写

不推荐：

	<link type="text/css" rel="stylesheet" href="base.css" />
	<script type="text/javascript" src="base.js"></script>

推荐：

	<link rel="stylesheet" href="base.css" />
	<script src="base.js"></script>

> 因为HTML5在引入CSS时，默认type值为text/css；在引入JavaScript时，默认type值为text/javascript

### 3.用双引号包裹属性值

所有的标签属性值必须要用双引号包裹，同时也不允许有的用双引号，有的用单引号的情况

不推荐：

	<a href=http://www.qunar.com class=home>去哪儿网</a>

推荐：

	<a href="http://www.qunar.com" class="home">去哪儿网</a>

### 4.属性值省略

非必须属性值可以省略

不推荐：

	<input type="text" readonly="readonly" />
	<input type="text" disabled="disabled" />

推荐：

	<input type="text" readonly />
	<input type="text" disabled />

> 这里的 readonly 和 disabled 属性的值是非必须的，可以省略不写，我们知道HTML5表单元素新增了很多类似的属性，如: required

### 5.嵌套

所有元素必须正确嵌套

* 不允许交叉
* 不允许inline元素包含block元素
* 不允许类似在ul下出现除了li外的其它子元素等等

不推荐：

	<span>
		<h1>这是一个块级h1元素</h1>
		<p>这是一个块级p元素</p>
	</span>
	<ul>
		<h3>xx列表</h3>
		<li>asdasdsdasd</li>
		<li>asdasdsdasd</li>
	</ul>

推荐：

	<div>
		<h1>这是一个块级h1元素</h1>
		<p>这是一个块级p元素</p>
	</div>
	<div>
		<h3>xx列表</h3>
		<ul>
			<li>asdasdsdasd</li>
			<li>asdasdsdasd</li>
		</ul>
	</div>

> 规则可参考：[嵌套规则](http://www.cs.tut.fi/~jkorpela/html/strict.html)。由于某些现实原因，在HTML5中对a元素做了一些变更，a元素除了可以包含inline元素外，也将可以包含block元素了。

### 6.标签闭合

所有标签必须闭合

不推荐：

	<div>balabala...
	<link rel="stylesheet" href="*.css">

推荐：

	<div>balabala...</div>
	<link rel="stylesheet" href="*.css" />

> 虽然有些标记没有要求必须关闭，但是为了避免出错的几率，要求必须全部关闭，省去判断某标记是否需要关闭的时间

### 7.使用img的alt属性

为img元素加上alt属性

不推荐：

	<img src="banner.jpg" />

推荐：

	<img src="banner.jpg" alt="520即将到来，爱就大声说出来" />

> alt属性的内容为对该图片的简要描述，这对于盲人用户和图像损毁都非常有意义，即无障碍。对于纯粹的装饰性图片，alt属性值可以留空，如 alt=""

### 8.使用label的for属性

为表单元素label加上for属性


不推荐：

	<label><input type="radio" name="color" value="0" />蓝色</label>
	<label><input type="radio" name="color" value="1" />粉色</label>

推荐：

	<label for="blue"><input type="radio" id="blue" name="color" value="0" />蓝色</label>
	<label for="pink"><input type="radio" id="pink" name="color" value="1" />粉色</label>

> for属性能让点击label标签的时候，同时focus到对应的 input 和 textarea上，增加响应区域

### 9.按模块添加注释

在每个模块开始和结束的地方添加注释

	<!-- 新闻列表模块 -->
	<div class="m-news g-mod"
	...
	<!-- /新闻列表模块 -->

	<!-- 排行榜模块 -->
	<div class="m-topic g-mod"
	...
	<!-- /排行榜模块 -->

> 注释内容左右两边保留和注释符号有1个空格位，在注释内容内不允许再出现中划线“-”，某些浏览器会报错
> 
> 注释风格保持与原生HTML的语法相似：成对出现 `<!-- comment --><!-- /comment -->`

### 10.格式

* 将每个块元素、列表元素或表格元素都放在新行
* inline元素视情况换行，以长度不超过编辑器一屏为宜
* 每个子元素都需要相对其父级缩进

不推荐：

	<div><h1>asdas</h1><p>dff<em>asd</em>asda<span>sds</span>dasdasd</p></div>

推荐：

	<div>
		<h1>asdas</h1>
		<p>dff<em>asd</em>asda<span>sds</span>dasdasd</p>
	</div>

### 11.语义化标签

* 根据HTML元素的本身用途去使用它们
* 禁止使用被废弃的用于表现的标签，如 center, font 等
* 部分在XHTML1中被废弃的标签，在HTML5中被重新赋予了新的语义，在选用时请先弄清其语义，如:b, i, u等

不推荐：

	<p>标题</p>

推荐：

	<h1>标题</h1>
	
> 虽然使用p标签，也可以通过CSS去定义它的外观和标题相同，但p标签本身的并不是表示标题，而是表示文本段落


<a name="css"></a>
## CSS约定



待修改完善。。。