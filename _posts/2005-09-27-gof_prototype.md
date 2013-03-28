---
layout: post
title: GoF创建型模式之Prototype
category: GoF_Patterns
---

使用工厂类创建一个和原型对象相同的类实例, Prototype模式里原型对象和工厂类通常是一个类, 所以应用Prototype模式的常见用法就是原型对象clone方法的调用.

Prototype结构图:

![prototype](/img/gof/prototype.gif)

JAVA语言和C++语言都很好的支持了Prototype模式, 在Java中就是clone()方法的使用, 在C++里Prototype模式就是赋值运算符的调用. 考虑到数据的完整复制，有时需要重载Java里的clone方法和重载C++里的赋值运算符, 以实现深拷贝.
