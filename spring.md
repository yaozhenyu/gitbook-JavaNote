# Spring

## 依赖注入 ：dependency injection\(DI\)

1、首先，什么叫依赖？类A中有一个字段是类型B的对象，可以叫做A依赖B；类A中某个方法参数是类型B的对象，也可以叫A依赖B；类A中有个局部变量是B类型的对象，也可以叫做A依赖B。

2、什么叫注入？类A依赖B，A获得B类对象的过程就叫做依赖注入。

## 控制反转：Inversion of Control\(IoC\)

A类依赖B类，A类对象获取B类对象时，不自己创建B类对象，而是交给Spring的IoC容器来创建，就叫做控制反转。 我们把被依赖的对象叫做bean，创建bean的Spring类有`ApplicationContext`和`BeanFactory`。这里应该用了工厂模式。

