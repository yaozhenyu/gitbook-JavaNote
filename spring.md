# Spring

## 依赖注入 ：dependency injection\(DI\)

1、首先，什么叫依赖？类A中有一个字段是类型B的对象，可以叫做A依赖B；类A中某个方法参数是类型B的对象，也可以叫A依赖B；类A中有个局部变量是B类型的对象，也可以叫做A依赖B。

2、什么叫注入？类A依赖B，A获得B类对象的过程就叫做依赖注入。

## 控制反转：Inversion of Control\(IoC\)

A类依赖B类，A类对象获取B类对象时，不自己创建B类对象，而是交给Spring的IoC容器来创建，就叫做控制反转。 我们把被依赖的对象叫做bean，创建bean的容器有`ApplicationContext（Interface）`和`BeanFactory`。这里应该用了工厂模式。

`ApplicationContext`的实现类有`ClassPathXmlApplicationContext和FileSystemXmlApplicationContext等 。`

配置bean的方法有

* Annotation-based configuration

* Java-based configuration

**基于XML配置**

Java代码：

```java
ApplicationContext context = new ClassPathXmlApplicationContext("services.xml", "daos.xml");
// retrieve configured instance
PetStoreService service = context.getBean("petStore", PetStoreService.class);
// use configured instance
List<String> userList = service.getUsernameList();
```

配置文件services.xml,如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <!-- services -->
    <bean id="petStore" class="org.springframework.samples.jpetstore.services.PetStoreServiceImpl">
        <property name="accountDao" ref="accountDao"/>
        <property name="itemDao" ref="itemDao"/>
    </bean>
</beans>
```

配置文件daos.xml,如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="accountDao"
        class="org.springframework.samples.jpetstore.dao.jpa.JpaAccountDao">
        <!-- additional collaborators and configuration for this bean go here -->
    </bean>
    <bean id="itemDao" class="org.springframework.samples.jpetstore.dao.jpa.JpaItemDao">
        <!-- additional collaborators and configuration for this bean go here -->
    </bean>
    <!-- more bean definitions for data access objects go here -->
</beans>
```

通过一个文件来管理其他的bean配置文件,用到`<import/>`元素来实现。

```
<beans>
    <import resource="services.xml"/>
    <import resource="resources/messageSource.xml"/>
    <import resource="/resources/themeSource.xml"/>

    <bean id="bean1" class="..."/>
    <bean id="bean2" class="..."/>
</beans>
```



