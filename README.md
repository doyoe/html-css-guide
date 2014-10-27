## 移动组出品



# HTML/CSS开发规范指南

## 目录

1. [规范概述](#intro)
2. [基本信息](#profile)
3. [通用约定](#general)
	* [文档目录结构](#directory)
	* [分离](#separate)
	* [缩进](#indentation)
	* [编码](#encoding)
	* [小写](#lowercase)
	* [注释](#comment)
	* [待办事项](#todo)
	* [行尾空格](#end-line-space)
	* [省略嵌入式资源协议头](#protocol-relative-url)
	* [代码有效性](#validator)
4. [HTML约定](#html)
	* [文档类型](#doctype)
	* [省略type属性](#type)
	* [省略属性值](#attribute)
	* [用双引号包裹属性值](#quots)
	* [嵌套](#nest)
	* [标签闭合](#close-tag)
	* [多媒体替代方案](#perceivable)
	* [有效操作](#friendly)
	* [按模块添加注释](#html-comment)
	* [格式](#format)
	* [语义化标签](#semantic)
5. [CSS约定](#css)
	* [文件引用](#link)
	* [命名-组成元素](#element)
	* [命名-词汇规范](#word)
	* [命名-缩写规范](#abbr)
	* [命名-前缀规范](#prefix)
	* [复用与重写](#reuse)
	* [id与class](#id)
	* [视觉封装](#packaging)
	* [规则与分号](#semicolon)
	* [0与单位](#unit)
	* [0与小数](#decimal)
	* [去掉uri中引用资源的引号](#non-quotes)
	* [HEX颜色值写法](#hex)
	* [属性书写顺序](#order)
	* [注释规范](#css-comment)
	* [hack规范](#hack)
	* [避免类型选择器](#type-selector)
	* [属性缩写与分拆](#override)
6. [图像约定](#img)
	* [图像压缩](#img-compress)
	* [背景图](#background-image)
	* [前景图](#image)
	* [Sprite](#sprite)
7. [结语](#end)

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
规范发起 | [杜瑶(@doyoe)](http://weibo.com/doyoe)
参与人群 | 酒店、机票、无线、目的地、度假、各SI
最后更新 | 2014.10.11

<a name="general"></a>
## 通用约定

<a name="directory"></a>
### 1.文档目录结构

```
|-- 项目名
	|-- src	
		|-- scripts      脚本目录
		|-- styles（Yo）  样式目录
			|-- lib   基础库
				|-- core      核心代码：reset 
				|-- element   元素
				|-- fragment  公用碎片
				|-- layout    布局
				|-- widget    组件
			|-- usage  项目具体实现
				|-- core      核心代码：桥接lib中的core，可以进行项目级扩展
				|-- fragment  项目公用碎片
				|-- module    模块
				|-- page      page桥接文件：src-list
				|-- export    page pack之后的文件
		|-- html    静态页面模板目录
		|-- bgimg   背景图目录（假设有的话）
		|-- image   前景图目录（假设有的话）
		|-- font    字体目录（假设有的话）
```

> `src`, `scripts`, `styles` 三个目录是为了和现有项目保持一致，避免修改过大，所以保持不变；

> `html` 目录，用于存放前端开发做的静态页面，以备查阅、备份、review或给后端套页面；

> `bgimg`, `image`, `font` 三个目录在Qunar一般不会直接存在，因为我们有source服务器，这些资源都会在那上面管理；不过特殊情况也会有，比如一些独立的项目，没有使用source的，那么就需要遵循这样的目录划分；

> 至于 `html`, `bgimg`, `image`, `font` 这几个目录为什么没有加 `s`，主要是因为不希望大家去想某个目录是否为复数，简单点就好；


<a name="separate"></a>
### 2.分离

结构（HTML）、表现（CSS）、行为分离（JavaScript）

> 将结构与表现、行为分离，保证它们之间的最小耦合，这对前期开发和后期维护都至关重要。

<a name="indentation"></a>
### 3.缩进

使用tab（4个空格宽度）来进行缩进，可以在IDE里进行设置

<a name="encoding"></a>
### 4.编码

* 以 UTF-8 无 BOM 编码作为文件格式；
* 在HTML中文档中用 `<meta charset="utf-8" />` 来指定编码；
* 不需要为CSS显示定义编码，因为它默认为utf-8；

<a name="lowercase"></a>
### 5.小写

* 所有的HTML标签必须小写
* 所有的HTML属性必须小写
* 所有的样式名及规则必须小写

<a name="comment"></a>
### 6.注释

尽可能的为你的代码写上注释。解释为什么要这样写，它是新鲜的方案还是解决了什么问题。

<a name="todo"></a>
### 7.待办事项

用 TODO 标示待办事项和正在开发的条目

	<!-- TODO: 图文混排 -->
	<div class="g-imgtext">
	<img src="1.png" alt="" />
	...

	/* TODO: 图文混排 comm: g-imgtext */
	.g-imgtext{ sRules }

<a name="end-line-space"></a>
### 8.行尾空格

删除行尾空格，这些空格没有必要存在

<a name="protocol-relative-url"></a>
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

<a name="validator"></a>
### 10.代码有效性

* 使用 [W3C HTML Validator](http://validator.w3.org/) 来验证你的HTML代码有效性；
* 使用 [W3C CSS Validator](http://jigsaw.w3.org/css-validator/) 来验证你的CSS代码有效性；

> 代码验证不是最终目的，真的目的在于让开发者在经过多次的这种验证过程后，能够深刻理解到怎样的语法或写法是非标准和不推荐的，即使在某些场景下被迫要使用非标准写法，也可以做到心中有数。

<a name="html"></a>
## HTML约定

<a name="doctype"></a>
### 1.文档类型

* 统一使用HTML5的标准文档类型：`<!DOCTYPE html>`

> HTML5文档类型具备前后兼容的特质，并且易记易书写

* 在文档doctype申明之前，不允许加上任何非空字符

> 任何出现在doctype申明之前的字符都将使得你的HTML文档进入非标准模式

* 不允许添加<meta>属性强制改变文档模式

> 避免出现不可控的问题

<a name="type"></a>
### 2.省略type属性

在调用CSS和JavaScript时，可以将type属性省略不写

不推荐：

	<link type="text/css" rel="stylesheet" href="base.css" />
	<script type="text/javascript" src="base.js"></script>

推荐：

	<link rel="stylesheet" href="base.css" />
	<script src="base.js"></script>

> 因为HTML5在引入CSS时，默认type值为text/css；在引入JavaScript时，默认type值为text/javascript

<a name="attribute"></a>
### 3.省略属性值

非必须属性值可以省略

不推荐：

	<input type="text" readonly="readonly" />
	<input type="text" disabled="disabled" />

推荐：

	<input type="text" readonly />
	<input type="text" disabled />

> 这里的 readonly 和 disabled 属性的值是非必须的，可以省略不写，我们知道HTML5表单元素新增了很多类似的属性，如: required

<a name="quots"></a>
### 4.用双引号包裹属性值

所有的标签属性值必须要用双引号包裹，同时也不允许有的用双引号，有的用单引号的情况

不推荐：

	<a href=http://www.qunar.com class=home>去哪儿网</a>

推荐：

	<a href="http://www.qunar.com" class="home">去哪儿网</a>

<a name="nest"></a>
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

<a name="close-tag"></a>
### 6.标签闭合

所有标签必须闭合

不推荐：

	<div>balabala...
	<link rel="stylesheet" href="*.css">

推荐：

	<div>balabala...</div>
	<link rel="stylesheet" href="*.css" />

> 虽然有些标记没有要求必须关闭，但是为了避免出错的几率，要求必须全部关闭，省去判断某标记是否需要关闭的时间

<a name="perceivable"></a>
### 7.多媒体替代方案

* 为img元素加上alt属性
* 为视频内容提供音轨替代
* 为音频内容提供字母替代等等

不推荐：

	<img src="banner.jpg" />

推荐：

	<img src="banner.jpg" alt="520即将到来，爱就大声说出来" />

> alt属性的内容为对该图片的简要描述，这对于盲人用户和图像损毁都非常有意义，即无障碍。对于纯粹的装饰性图片，alt属性值可以留空，如 alt=""

<a name="friendly"></a>
### 8.有效操作

为表单元素label加上for属性

不推荐：

	<label><input type="radio" name="color" value="0" />蓝色</label>
	<label><input type="radio" name="color" value="1" />粉色</label>

推荐：

	<label for="blue"><input type="radio" id="blue" name="color" value="0" />蓝色</label>
	<label for="pink"><input type="radio" id="pink" name="color" value="1" />粉色</label>

> for属性能让点击label标签的时候，同时focus到对应的 input 和 textarea上，增加响应区域

<a name="html-comment"></a>
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

> 注释内容左右两边保留和注释符号有1个空格位，在注释内容内不允许再出现中划线“-”，某些浏览器会报错。
> 
> 注释风格保持与原生HTML的语法相似：成对出现 `<!-- comment --><!-- /comment -->`

<a name="format"></a>
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

<a name="semantic"></a>
### 11.语义化标签

* 根据HTML元素的本身用途去使用它们
* 禁止使用被废弃的用于表现的标签，如 center, font 等
* 部分在XHTML1中被废弃的标签，在HTML5中被重新赋予了新的语义，在选用时请先弄清其语义，如:b, i, u等

不推荐：

	<p>标题</p>

推荐：

	<h1>标题</h1>
	
> 虽然使用p标签，也可以通过CSS去定义它的外观和标题相同，但p标签本身的并不是表示标题，而是表示文本段落

> 参阅：[HTML5 Elements](http://www.w3.org/TR/html5/) 



<a name="css"></a>
## CSS约定

<a name="link"></a>
### 1.文件引用

* 一律使用link的方式调用外部样式

> 一般情况下，在页面中只允许使用 `<link />` 标签来引用CSS文件，

<a name="element"></a>
### 2.命名-组成元素

* 命名必须由单词、中划线①或数字组成；
* 不推荐使用拼音来作为样式名，尤其是缩写的拼音、拼音与英文的混合

不推荐：

	.xiangqing{}
	.news_list{}
	.zhuti{}

推荐：

	.detail{}
	.news-list{}
	.topic{}

> ①我们使用中划线 “-” 作为连接字符，而不是下划线 "_"。
> 
> 我们知道2种方式都有不少支持者，但 "-" 能让你少按一次shift键，并且更符合CSS原生语法，所以我们只选一种目前业内普遍使用的方式

<a name="word"></a>
### 3.命名-词汇规范

* 不依据表现形式来命名
* 可根据内容来命名
* 可根据功能来命名

不推荐：

	left, right, center, red, black

推荐：

	nav, news, type, search

<a name="abbr"></a>
### 4.命名-缩写规范

* 保证缩写后还能较为清晰保持原单词所能表述的意思；
* 使用业界熟知的或者约定俗成的；

不推荐：

	navigation   =>  navi	
	header       =>  head
	description  =>  des

推荐：

	navigation   =>  nav	
	header       =>  hd
	description  =>  desc

<a name="prefix"></a>
### 5.命名-前缀规范

前缀|说明|示例
---|---|---|
g-|全局通用样式命名，前缀g全称为global，一旦修改将影响全站样式|g-mod
m-|模块命名方式|m-detail
ui-|组件命名方式|ui-selector
J-|所有用于纯交互的命名，不涉及任何样式规则。JSer拥有全部定义权限|J-switch

* 选择器必须是以某个前缀开头

不推荐：

	.info{}
	.current{}
	.news{}
	
> 因为这样将给我们带来不可预知的管理麻烦以及沉重的历史包袱。你永远也不会知道哪些样式名已经被用掉了，如果你是一个新人，你可能会遭遇，你每定义个样式名，都有同名的样式已存在，然后你只能是换样式名或者覆盖规则。

推荐：

	.m-detail .info{}
	.m-detail .current{}
	.m-detail .news{}
	
> 所有的选择器必须是以 g-, m-, ui- 等有前缀的选择符开头的，意思就是说所有的规则都必须在某个相对的作用域下才生效，尽可能减少全局污染。

J- 这种级别的className完全交由JSer自定义，但是命名的规则也可以保持跟重构一致，比如说不能使用拼音之类的

<a name="reuse"></a>
### 6.复用与重写

参见模块化设计

<a name="id"></a>
### 7.id与class

* id只可能出现在document layout级别上，意思就是说页面工程师几乎没有写id的场景，除了layout搭建者外

<a name="packaging"></a>
### 8.视觉封装

* 原生CSS代码书写不分行
* 不要以缩进的方式来体现层级关系

不推荐：

	.g-box{ sRules; }
		.g-box-hd .xx{ sRules; }
			.g-box-hd .xx .aa{ sRules; }

推荐：

	.g-box{ sRules; }
	.g-box-hd .xx{ sRules; }
	.g-box-hd .xx .aa{ sRules; }

> 这些都是为了达到简易视觉封装和一致性，让肉眼可以迅速以开头选择器作为检索的流从而主观识别区块

<a name="semicolon"></a>
### 9.规则与分号

* 每条规则结束后都必须加上分号

不推荐：

	body{
		margin: 0;
		padding: 0;
		font-size: 14px
	}

推荐：

	body{
		margin: 0;
		padding: 0;
		font-size: 14px;
	}

<a name="unit"></a>
### 10.0与单位

* 如果属性值为0，则不需要为0加单位

不推荐：

	body{
		margin: 0px;
		padding: 0px;
	}

推荐：

	body{
		margin: 0;
		padding: 0;
	}

<a name="decimal"></a>
### 11.0与小数

* 如果是0开始的小数，前面的0可以省略不写

不推荐：

	body{
		opacity: 0.6;
		text-shadow: 1px 1px 5px rgba(0, 0, 0, 0.5);
	}

推荐：

	body{
		opacity: .6;
		text-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
	}

<a name="non-quotes"></a>
### 12.去掉uri中引用资源的引号

* 不要在url()里对引用资源加引号

不推荐：

	body{ background-image: url("sprites.png"); }
	@import url("global.css");

推荐：

	body{ background-image: url(sprites.png); }
	@import url(global.css);

<a name="hex"></a>
### 13.HEX颜色值写法

* 将所有的颜色值小写
* 可以缩写的缩写至3位

不推荐：

	body{ background-color: #FF0000; }

推荐：

	body{ background-color: #f00; }

<a name="order"></a>
### 14.属性书写顺序

* 遵循先布局后内容的顺序。

```
.g-box{
　　　display: block;
　　　float: left;
　　　width: 500px;
　　　height: 200px;
　　　margin: 10px;
　　　padding: 10px;
　　　border: 10px solid;
　　　background: #aaa;
　　　color: #000;
　　　font: 14px/1.5 sans-serif;
}
```

> 这个应该好理解，比如优先布局，我们知道布局属性有 display, float, overflow 等等；内容次之，比如 color, font, text-align 之类。

* 组概念。

拿上例的代码来说，如果我们还需要进行定位及堆叠，规则我们可以改成如下： 

```
.g-box{
　　　display: block;
　　　position: relative;
　　　z-index: 2;
　　　top: 10px;
　　　left: 100px;
　　　float: left;
　　　width: 500px;
　　　height: 200px;
　　　margin: 10px;
　　　padding: 10px;
　　　border: 10px solid;
　　　background: #aaa;
　　　color: #000;
　　　font: 14px/1.5 sans-serif;
}
```

> 从代码中可以看到，我们直接将z-index, top, left 紧跟在 position 之后，因为这几个属性其实是一组的，如果去掉position，则后3条属性规则都将失效。

* 私有属性在前标准属性在后

```
.g-box{
　　　-webkit-box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
　　　   -moz-box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
　　　     -o-box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
　　　        box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
}
```

> 当有一天你的浏览器升级后，可能不再支持私有写法，那么这时写在后面的标准写法将生效，避免无法向后兼容的情况发生。

<a name="css-comment"></a>
### 15.注释规范

* 保持注释内容与星号之间有一个空格的距离

**普通注释（单行）**

	/* 普通注释 */

**区块注释**

	/**
	 * 模块: m-detail
	 * author: joy.du
	 * edit: 2013.12.19
	 */

> 有特殊作用的规则一定要有注释说明
> 应用了高级技巧的地方一定要注释说明

<a name="hack"></a>
### 16.hack规范

* 尽可能的减少对Hack的使用和依赖，如果在项目中对Hack的使用太多太复杂，对项目的维护将是一个巨大的挑战；
* 使用其它的解决方案代替Hack思路；
* 如果非Hack不可，选择稳定且常用并易于理解的；

```
.test{
　　　color: #000;       /* For all */
　　　color: #111\9;     /* For all IE */
　　　color: #222\0;     /* For IE8 and later, Opera without Webkit */
　　　color: #333\9\0;   /* For IE8 and later */
　　　color: #444\0/;    /* For IE8 and later */
　　　[;color: #555;];   /* For Webkit, IE7 and earlier */
　　　*color: #666;      /* For IE7 and earlier */
　　　_color: #777;      /* For IE6 and earlier */
}
```

* 严谨且长期的项目，针对IE可以使用条件注释作为预留Hack或者在当前使用

IE条件注释语法：
<!--[if <keywords>? IE <version>?]>
<link rel=”stylesheet” href=”*.css” />
<![endif]-->

语法说明：

```
<keywords>
if条件共包含6种选择方式：是否、大于、大于或等于、小于、小于或等于、非指定版本
是否：指定是否IE或IE某个版本。关键字：空
大于：选择大于指定版本的IE版本。关键字：gt（greater than）
大于或等于：选择大于或等于指定版本的IE版本。关键字：gte（greater than or equal）
小于：选择小于指定版本的IE版本。关键字：lt（less than）
小于或等于：选择小于或等于指定版本的IE版本。关键字：lte（less than or equal）
非指定版本：选择除指定版本外的所有IE版本。关键字：!
```

```
<version>

目前的常用IE版本为6.0及以上，推荐酌情忽略低版本，把精力花在为使用高级浏览器的用户提供更好的体验上，另从IE10开始已无此特性
```

<a name="type-selector"></a>
### 17.避免类型选择器

* 避免出现标签名与ID或class组合的选择器
* 太多这种写法会让你的CSS效率变得糟糕

不推荐：

	div#doc{ sRules; }
	li.first{ sRules; }

推荐：

	#doc{ sRules; }
	.first{ sRules; }

<a name="override"></a>
### 18.属性缩写与分拆

* 无继承关系时，使用缩写
* 存在继承关系时，使用分拆方式
* 根据规则条数选择缩写和拆分

**无继承关系时，使用缩写**

不推荐：

```
body{
　　　margin-top: 10px;
　　　margin-right: 10px;
　　　margin-bottom: 10px;
　　　margin-left: 10px;
}
```

推荐：

```
body{
　　　margin: 10px;
}
```

**存在继承关系时，使用分拆方式**

不推荐：

```
.m-detail{
　　　font: bold 12px/1.5 arial, sans-serif;
}
.m-detail .info{
　　　font: normal 14px/1.5 arial, sans-serif;
}
```

推荐：

```
.m-detail{
　　　font: bold 12px/1.5 arial, sans-serif;
}
.m-detail .info{
　　　font-weight: normal;
　　　font-size: 14px;
}
```

> 在存在继承关系的情况下，只将需要变更的属性重定义，不进行缩写，避免不需要的重写的属性被覆盖定义

**根据规则条数选择缩写和拆分**

不推荐：

```
.m-detail{
　　　border-width: 1px;
　　　border-style: solid;
　　　border-color: #000 #000 #f00;
}
```

推荐：

```
.m-detail{
　　　border: 1px solid #000;
　　　border-bottom-color: #f00;
}
```

<a name="img"></a>
## 图像约定

<a name="img-compress"></a>
### 1.图像压缩

所有图片必须经过一定的压缩和优化才能发布

<a name="background-image"></a>
### 2.背景图

* 使用PNG格式而不是GIF格式，因为PNG格式色彩更丰富，还能提供更好的压缩比
* 在需要兼容IE6的项目中，尽可能选择PNG8，而不是使用PNG24+滤镜

<a name="image"></a>
### 3.前景图

* 内容图片建议使用JPG，可以拥有更好地显示效果
* 装饰性图片使用PNG

<a name="sprite"></a>
### 4.Sprite

* CSS Sprite是一种将数个图片合成为一张大图的技术（既可以是背景图也可以是前景图），然后通过偏移来进行图像位置选取
* CSS Sprite可以减少http请求


<a name="end"></a>
## 结语

坚持一致性的原则。
一个团队的代码风格如果统一了，首先可以培养良好的协同和编码习惯，其次可以减少无谓的思考，再次可以提升代码质量和可维护性。
统一的代码风格，团队内部阅读或编辑代码，将会变得非常轻松，因为组员都用一致思维环境。

待修改完善。。。