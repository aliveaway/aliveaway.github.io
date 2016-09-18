---
layout: post
title: java包装类、日期类、数学类
category: Android
tags: 包装类
---

# 包装类

| 基本类型   |      包装类     |
|----------|:-------------:|
| byte |  Byte |
| short |    Short   |
| int | Integer |
| long | Long |
| boolean | Boolean |
| char | Character |
| float | Float |
| double | Double |

# 应用

1. 实现基本类型和字符串类型的转换

2. 字符串类型转基本类型

把十进制转成其它进制，得到的是其它进制形式的字符串

Integer.toHexString() 

Integer.toOctalString()

Integer.toBinaryString()

其它进制转十进制

Integer.parseInt(数据，进制)，返回值int类型

{% highlight java linenos %}
Integer i = new Integer(23);//jdk1.5之前
int num = i.intValue();
System.out.println(num);
//jdk1.5开始
Integer n = 23;//自动装箱
n = n + 5;//自动拆箱，n = n.intValue() + 5 = 28,在自动装箱new Integer(28)

Integer x = 127;
Integer y = 127;
System.out.println(x ==y);//true

Integer x1 = 128;
Integer y1 = 128;
System.out.println(x ==y);//false

{% endhighlight %}

> 一个数如果在一个字节允许范围内，如果之前定义过，那么再定义时使用以前的。

# 打包导入

> 解决class同名的问题，解决的入手点根据在同一个文件夹下，不能有同名的文件入手

## 打包命令

`javac -d . Person.java`

在当前路径编译打包Person类

# 权限

|   |      private    | 默认 | protected | public |
|----------|:-------------:|:-------------:|:-------------:|:-------------:|
| 同一个类中 | yes | yes | yes | yes |
| 同一个包中 | no | yes | yes | yes |
| 不同的包中有继承关系 | no | no | yes | yes |
| 不同的包没有继承关系 | no | no | no | yes |

# 日期类

java.lang包中的类是自动导入的，所以Object不需要导入包。
java.util.Date

{% highlight java linenos %}
public class Demo {
    public static void main(String[] args) {
        Date date = new Date();
        System.out.println(date);

        //long转换Date
        long  time = date.getTime();
        System.out.println(time);

        Date d = new Date(System.currentTimeMillis());
        System.out.println(d);

    }
}

{% endhighlight %}

输出的结果：

Sun Sep 18 18:27:19 CST 2016
1474194439026
Sun Sep 18 18:27:19 CST 2016

{% highlight java linenos %}
public class Demo2 {
    public static void main(String[] args) {
        //得到一个日期时间格式化对象
        DateFormat df = DateFormat.getDateTimeInstance();

        //创建需要被格式化的日期对象
        Date d = new Date();

        // 使用DateFormat对象格式化日期时间
        String time = df.format(d);
        System.out.println(time);
    }
}
{% endhighlight %}

> 输出的结果：2016-9-18 18:34:18s

通过给getDateTimeInstance()设置参数可以得到不同的日期字符串

{% highlight java linenos %}
public class Demo2 {
    public static void main(String[] args) {
        //得到一个日期时间格式化对象
        DateFormat df = DateFormat.getDateTimeInstance(DateFormat.FULL,DateFormat.FULL);

        //创建需要被格式化的日期对象
        Date d = new Date();

        // 使用DateFormat对象格式化日期时间
        String time = df.format(d);
        System.out.println(time);
    }
}
{% endhighlight %}

> 2016年9月18日 星期日 下午06时43分04秒 CST,这是最全的时间日期格式的字符串，其它几个参数设置类似，参考API

### 按照自己想要的方式设置

SimpleDateFormat类，按照我们自己指定的来显示,构造方法有个带字符串的参数，用于指定格式

{% highlight java linenos %}
SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd E HH:mm:ss");
Date dt = new Date();
String forStr = format.format(dt);
System.out.println(forStr);
{% endhighlight %}

> 结果：2016-09-18 星期日 18:51:22
