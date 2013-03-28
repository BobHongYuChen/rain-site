---
layout: post
title: GoF行为型模式之Mediator
category: GoF_Patterns
---

Mediator模式用于解决多个类之间的复杂关系以提高类的使用效率。如果很多个类之间需要相互访问，他们的访问关系是一种网状调用关系，这时可以考虑引入Mediator类，所有的类都与Mediator发生关系而不直接与对方发生关系，这样网状关系将被调整为一对多的关系，所有调用关系由Mediator负责协调，这样可以使得调用关系简单，也降低了原先的多个类之间的耦合关系。
