---
layout: post
title: 进程和线程
category: Android
tags: 进程线程
---

# 基础概念

进程：正在进行中的程序，一个应用就代表一个进程。windows任务管理器里面的每一个任务都是一个进程。

线程：举个例子，360安全卫士就是那个进程，电脑清理和优化加速。我在360里面点击电脑清理，一个线程开始执行，这是我再点击优化加速，另一个
线程启动。电脑清理和优化加速就是线程，它们通过轮流抢占cpu，交替执行各自的代码，实现感官上的同时执行，直到各自的代码执行完毕，线程结束
(从内存消失)。

> 进程可以看作是线程的集合，进程执行的本质是里面线程的执行，进程自己不能执行。

# 垃圾回收

jvm是个多线程程序，主线程负责执行代码，垃圾回收线程负责回收垃圾对象。在Object类里面定义了方法finalize(),垃圾线程执行该方法清理垃圾对象。
每个线程需要执行的代码叫做任务代码，都有它的存储位置。线程随着任务的存在而存在，随着任务的结束而结束。

{% highlight java linenos %}
public class Demo3 {

    public static void main(String[] args) {
        new Test();
        new Test();
        new Test();

        System.gc();//垃圾回收线程执行

        System.out.println("垃圾回收完毕");
    }
}

class Test {

    @Override
    protected void finalize() throws Throwable {
        System.out.println("垃圾回收执行");
    }
}
{% endhighlight %}

Thread.currentThread()返回当前占用cpu的线程