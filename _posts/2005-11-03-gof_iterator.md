---
layout: post
title: GoF行为型模式之Iterator
category: GoF_Patterns
---

Iterator模式用于遍历容器类, 由于Iterator模式非常常用, 因此已经被整合在很多流行的语言框架里.

在JAVA里, 这个模式已经被整合入Collection框架中，Collection里的很多容器类都提供了方法返回一个Iterator, 因此只要将对象装入容器类中，就可以直接使用Iterator进行对象遍历。

在C++的STL中，也已经封装了几个标准的Iterator模板，将对象放入STL容器后，使用对应的Iterator遍历即可。
