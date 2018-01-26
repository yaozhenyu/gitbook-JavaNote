1、元注解

元注解是指注解的注解。包括  @Retention @Target @Document @Inherited四种。

**@Retention**

Retention 的英文意为保留期的意思。当 @Retention 应用到一个注解上的时候，它解释说明了这个注解的的存活时间。

* RetentionPolicy.SOURCE 注解只在源码阶段保留，在编译器进行编译时它将被丢弃忽视。

* RetentionPolicy.CLASS 注解只被保留到编译进行的时候，它并不会被加载到 JVM 中。

* RetentionPolicy.RUNTIME 注解可以保留到程序运行的时候，它会被加载进入到 JVM 中，所以在程序运行时可以获取到它们。

**@Targe**注解

@Target 指定了注解运用的地方。

* ElementType.ANNOTATION\_TYPE 可以给一个注解进行注解

* ElementType.CONSTRUCTOR 可以给构造方法进行注解

* ElementType.FIELD 可以给属性进行注解

* ElementType.LOCAL\_VARIABLE 可以给局部变量进行注解

* ElementType.METHOD 可以给方法进行注解

* ElementType.PACKAGE 可以给一个包进行注解

* ElementType.PARAMETER 可以给一个方法内的参数进行注解

* ElementType.TYPE 可以给一个类型进行注解，比如类、接口、枚举

### @Inherited {#inherited}

Inherited 是继承的意思，但是它并不是说注解本身可以继承，而是说如果一个超类被 @Inherited 注解过的注解进行注解的话，那么如果它的子类没有被任何注解应用的话，那么这个子类就继承了超类的注解。

2、自定义注解（@interface）

```
@Target({ElementType.FIELD, ElementType.METHOD}) // 指定注解可以使用的位置
@Retention(RetentionPolicy.RUNTIME) // 运行时读取注解信息（不加无法读取）
public @interface MyAnnotation {

    String[] value1() default "abc";
}
```



