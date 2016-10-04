---
layout: post
title: js函数
category: web开发
tags: js-func
---

# 简介

js中的函数对应Function，和数组类似。每个函数都是一个Function类型的对象，函数是引用类型，既然是引用类型，就有属性和方法。

# 创建方法

1.普通方式

{% highlight javascript linenos %}
<script type="text/javascript">
	function fun(num1,num2) {
		return num1 + num2;
	}
</script>
{% endhighlight %}

2.变量方式

{% highlight javascript linenos %}
<script type="text/javascript">
	var fun = function() {
		return "hello";
	}
</script>
{% endhighlight %}

3.new的方式(不建议使用，运行性能较以上两个低)

{% highlight javascript linenos %}
<script type="text/javascript">
	var fun = new Function("n1","n2","return n1 + n2");
</script>
{% endhighlight %}

函数可以作为参数传递给另一个函数

# 内部属性

1.arguments属性，指向一个类似数组但不是数组的对象，存储的是实际传递给函数的参数，而不限于函数定义的参数列表。

例子：

{% highlight javascript linenos %}
<script type="text/javascript">
	function show(a,b){
		if (arguments.lenght == 2) {
			return a + b;
		} else if (arguments == 3) {
			return arguments[0] + arguments[1] + arguments[2];
		}
	}

	show("hello","world","roman");
</script>
{% endhighlight %}

2.lenght属性，定义函数时参数个数

3.arguments对象中的callee属性，表示函数对象本身的引用

阶乘

{% highlight javascript linenos %}
<script type="text/javascript">
	function jie(n){
		if (n == 1) {
			return 1;
		} else {
			reutn n * arguments.call(n - 1);
		}
	}

	show("hello","world","roman");
</script>
{% endhighlight %}

这样写及时函数名称改变也不会出错。

# 局部变量和全局变量

*如果局部变量和全局变量同名，用局部变量*

# this的理解

{% highlight javascript linenos %}
<script type="text/javascript">
	function show(name){
		alert(name);
	}
	var f = show;
	f("lily");
</script>
{% endhighlight %}

> show是函数对象的引用，存储的是函数对象内存的地址。第5行的赋值就是简单的变量赋值。

{% highlight javascript linenos %}
<script type="text/javascript">
	var name = "li";
	function show(){
		alert(name);
	}
	show();//this指向window对象
</script>
{% endhighlight %}

# 函数内部方法

Function内部有个prototype属性，该属性有两个方法，call()和apply()。作用：改变调用函数的对象