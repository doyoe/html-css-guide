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

<a name="css"></a>
## CSS约定



待修改完善。。。