---
layout: post
title: java泛型
category: Android
tags: 泛型
---

# 泛型解决的问题

{% highlight java linenos %}

{% endhighlight %}

> 问题会在编译时期被发现，而不是执行的时候。通过<数据类型>接收一种引用数据类型，编译时会检查集合中存储的对象是否是该类型的，
如果不是，编译时不通过，从而把运行问题转移到编译时期，提高了程序安全性。使用泛型不需要强制类型转换。泛型擦除：泛型是在编译时期的，
所以在class字节码文件中不存在泛型。

# 在类上定义泛型

# 泛型通配符?

# 泛型限定

？ extends E  可以接收E类型或E类型的子类型

? super E  可以接收E类型或E类型的父类型

# HashSet排序

> String类默认排序方式是从小到大，现在我们要让String从短到长排序，实现Comparetor接口(自定义排序)。

