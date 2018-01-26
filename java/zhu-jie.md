# 注解

1、元注解

元注解是指注解的注解。包括  @Retention @Target @Document @Inherited四种。

2、自定义注解

```
@Retention(RetentionPolicy.RUNTIME) // 运行时读取注解信息
public @interface MyAnnotation {

    String[] value1() default "abc";
}


```



