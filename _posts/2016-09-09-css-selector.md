---
layout: post
title: css基础-选择器
category: web开发
tags: 选择器
description: 
---
# 选择器种类
* 通配选择器  
* 标签选择器
* 类选择器
* ID选择器
* 群组选择器
> 成群结对的出现  

``` css
<style type="text/css">
	p,table,#div,.main{
		background-color: #999;
		margin: 0
	}
</style>
```

* 后代选择器

``` html
<table>
	<tr>
		<td>1</td>
		<td>2</td>
	</tr>
	<tr>
		<td>3</td>
		<td>4</td>
	</tr>
</table>
```
> 如上图，table是父，tr和td都是它的后代，后代选择器代码如下

``` css
<style type="text/css">
	table tr td{}
	table td{}
</style>
```

* 子代选择器  

``` html
<table>
	<tr>
		<td>1</td>
	</tr>
</table>
```

> tr是table的子，td是tr的子，但td不是table的子(是孙子),**子代选择器不能跨两代，像这样是不对的table`>`tr`>`td**

``` css
<style type="text/css">
	tr>td{background: #999}
</style>
```

* 属性选择器  

``` html
<div id="main" class="contain"></div>
```

``` css
<style type="text/css">
	[title]{
		background-color: #999;
		margin: 0
	}
</style>
```

# 相邻兄弟选择器

``` html
<table>
	<tr>
		<td>1</td>
		<td>2</td>
	</tr>
	<tr>
		<td>3</td>
		<td>4</td>
	</tr>
</table>
```

> 1,2是相邻兄弟，3,4是相邻兄弟，2个tr是相邻兄弟，1和3,4不是相邻兄弟，同理2和3,4也不是相邻兄弟。
如下选择器，把2,4变成浅灰色。网页从上往下加载，看到第一个td为1，它的兄弟为2，背景变成灰色，4同理。


``` css
<style type="text/css">
	td + td{background: #999}
</style>
```

* 伪类
> 应用为超链接点击前后的样式，`a:link`点击前样式，`a:visited`点击后样式，`a:hover`鼠标悬停样式，`a:active`点击时样式
顺序按照一次出现的顺序书写在css中，w3c规定，否则可能出问题。