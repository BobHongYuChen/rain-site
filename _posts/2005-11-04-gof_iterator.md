---
layout: post
title: GoF行为型模式之Iterator，Mediator，Interpreter，Memento，State，Chain of Responsibility，Visitor
category: GoF_Patterns
---

下面几个模式要么用的不多，要么在各种语言里已经有很常见和自然的实现了，这里只做一些简单介绍。

##### Interator

Iterator模式用于遍历容器类, 由于Iterator模式非常常用, 因此已经被整合在很多流行的语言框架里.

在JAVA里, 这个模式已经被整合入Collection框架中，Collection里的很多容器类都提供了方法返回一个Iterator, 因此只要将对象装入容器类中，就可以直接使用Iterator进行对象遍历。

在C++的STL中，也已经封装了几个标准的Iterator模板，将对象放入STL容器后，使用对应的Iterator遍历即可。

##### Mediator

Mediator模式用于解决多个类之间的复杂关系以提高类的使用效率。如果很多个类之间需要相互访问，他们的访问关系是一种网状调用关系，这时可以考虑引入Mediator类，所有的类都与Mediator发生关系而不直接与对方发生关系，这样网状关系将被调整为一对多的关系，所有调用关系由Mediator负责协调，这样可以使得调用关系简单，也降低了原先的多个类之间的耦合关系。

Message Bus就是一种mediator模式的应用。

##### Interpreter

Interpreter模式多用于实现语言解释器，在应用软件里的使用面不是很广。

##### Memento

Memento很简单, 是一个保存另外一个对象内部状态拷贝的对象.这样以后就可以将该对象恢复到原先保存的状态.

##### State

不同的状态,不同的行为;或者说,每个状态有着相应的行为.

State模式结构图:

![](/img/gof/state.gif)

有限状态机就是state模式的应用。

##### Chain of Responsibility

Chain of Responsibility模式是用一系列类(classes)试图处理一个请求request,这些类之间是一个松散的耦合,唯一共同点是在他们之间传递request. 也就是说，来了一个请求，A类先处理，如果没有处理，就传递到B类处理，如果没有处理，就传递到C类处理，就这样象一个链条(chain)一样传递下去。

Servlet里的HTTP Filter机制和WTL里的消息传递都有点类似责任链模式.

##### Visitor

