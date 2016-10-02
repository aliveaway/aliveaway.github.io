---
layout: post
title: js时间日期
category: web开发
tags: js日期
---

# 日期的创建

{% highlight javascript linenos %}
<script type="text/javascript">
	var date = new Date();//系统当前时间

	var d1 = new Date(1000);//1970,1,1,8:00开始走过1s	

	//内部使用Date.parse()得到毫秒数
	var d2 = new Date("4/18/2008");//2008.04.18

</script>
{% endhighlight %}

因为内部使用Date.parse()，存在浏览器兼容问题。日期书写不正确不同浏览器的表现不一样注意。

# 时间和日期(其它的创建方法)

Date.UTC()国际协调时间（时间统一时间）解决兼容问题

# 常用方法

1.通用方法

toString,toLacleString,valueOf

2.日期格式化方法

toDateString,toTimeString,toLocaleDateString,toLocaleTimeString,toUTCString,

3.组件方法

单独获取年，月，日等。一系列的get和set方法
