---
layout: post
title: 适配器模式
category: 设计模式
tags: 设计模式
description:
---

# 解决问题

解决接口和类不兼容问题

> 适配器设计模式主要是为了解决类和接口一起工作不兼容的问题。拿生活中的例子来类比，
例如，我的笔记本的电源适配器，它的插头是三个脚的，而我目前身边只有一个两孔的插座，那么
我要想使用电源，就必须有一个东西能把3孔插头和2孔插座联系起来工作，这个把它们联系起来的
东西，就和我要说的适配器类似。

1.组合方式实现插座适配器

首先定义一个三相插座的接口，里面有个接口使用使用三相电流供电

``` java
public interface ThreePluginIf {
    //使用三相电流供电
    public void powerWithThree();
}
```
不同国家电流分类不同，假设我有个国标二相电流类，它有个方法，如下

``` java
public class GBTwoPlug {
    public void powerWithTwo() {
        System.out.println("二相电流供电");
    }
}
```

笔记本类如下，笔记本能充电，有个charge方法。构造方法传入三相电接口，二相插座转三相需要一个中间类，
我叫它适配器(TwoPlugAdapter)

``` java
public class NoteBook {
    private ThreePluginIf threePluginIf;

    public NoteBook(ThreePluginIf threePluginIf) {
        this.threePluginIf = threePluginIf;
    }

    public void charge() {
        threePluginIf.powerWithThree();
    }

    public static void main(String[] args) {
        GBTwoPlug two = new GBTwoPlug();
        ThreePluginIf threePlug = new TwoPlugAdapter(two);
        NoteBook noteBook = new NoteBook(threePlug);
        noteBook.charge();
    }

}
```

适配器类实现了三相的接口，使用组合的方法，其实用二相类实现实际的功能

``` java
public class TwoPlugAdapter implements ThreePluginIf {
    private GBTwoPlug two;

    public TwoPlugAdapter(GBTwoPlug two) {
        this.two = two;
    }

    @Override
    public void powerWithThree() {
        two.powerWithTwo();
    }
}
```

2.继承方式实现插座适配器

和组合的代码类似，继承方式实现插座适配器只需要增加一个适配器,
继承二相类并实现三相接口

``` java
public class TwoPlugAdapterExtends extends GBTwoPlug implements ThreePluginIf {

    @Override
    public void powerWithThree() {
        System.out.println("借助继承实现");
        this.powerWithTwo();
    }
}
```

二种方法的区别

组合方式:若所适配的类新添加子类，用一个适配器都能适配

继承方式:新添加子类要额外新建适配器

透明

重用

低耦合