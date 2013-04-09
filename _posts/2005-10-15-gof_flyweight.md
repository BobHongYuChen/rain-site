---
layout: post
title: GoF结构型模式之Flyweight
category: GoF_Patterns
---

Flyweight模式是为了避免大量小粒度对象的创建和销毁所造成的性能的消耗。

Flyweight结构图:

![](/img/gof/flywe050.gif)

JDK中java.lang.Integer#valueOf(int)，java.lang.Boolean#valueOf(boolean)也是Flyweight模式的一种应用。