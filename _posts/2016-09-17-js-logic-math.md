---
layout: post
title: js逻辑运算符
category: web开发
tags: javascript
description: 
---

# 注意事项

&& ||

{% highlight javascript linenos %}
<script type="text/javascript">
	var a = 5,b = 6;
	alert(a<1 && ++b>5);//左边的为false,不再计算表达式右边
	alert(b);//b=6,表达式没有计算

	alert(a>1 || ++b>5);//表达式左边为true,右边的不再计算
	alert(b);//b=6

	//0相当鱼于false,非0是true
	alert(0&&6);//false
	alert(3&&6);//6

	alert("" && "hello");//"";
	alert("hello" && "world");//""相当于false,非空相当于true

</script>
{% endhighlight %}
