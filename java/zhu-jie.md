# 注解

1、元注解

元注解是指注解的注解。包括  @Retention @Target @Document @Inherited四种。

**@Retention**

Retention 的英文意为保留期的意思。当 @Retention 应用到一个注解上的时候，它解释说明了这个注解的的存活时间。

* RetentionPolicy.SOURCE 注解只在源码阶段保留，在编译器进行编译时它将被丢弃忽视。

* RetentionPolicy.CLASS 注解只被保留到编译进行的时候，它并不会被加载到 JVM 中。

* RetentionPolicy.RUNTIME 注解可以保留到程序运行的时候，它会被加载进入到 JVM 中，所以在程序运行时可以获取到它们。

2、自定义注解（@interface）

```
@Target({ElementType.FIELD, ElementType.METHOD}) // 指定注解可以使用的位置
@Retention(RetentionPolicy.RUNTIME) // 运行时读取注解信息（不加无法读取）
public @interface MyAnnotation {

    String[] value1() default "abc";
}
```



