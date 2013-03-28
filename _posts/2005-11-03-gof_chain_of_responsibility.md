---
layout: post
title: GoF行为型模式之Chain of Responsibility
category: GoF_Patterns
---

Chain of Responsibility模式是用一系列类(classes)试图处理一个请求request,这些类之间是一个松散的耦合,唯一共同点是在他们之间传递request. 也就是说，来了一个请求，A类先处理，如果没有处理，就传递到B类处理，如果没有处理，就传递到C类处理，就这样象一个链条(chain)一样传递下去。

Servlet里的HTTP Filter机制和WTL里的消息传递都有点类似责任链模式.
