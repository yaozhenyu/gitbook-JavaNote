# Java

关键字：static

```
package example;

public class TestStatic {
    // static所在语句只执行一次。
    public static TestStatic st = new TestStatic();
    public TestStatic(){
        System.out.println("st");
    }
}
```

# java中import static和import的区别

import static（静态导入）是JDK1.5中的新特性，导入类中的**静态方法或静态成员变量**，在引用类中可以直接使用，不用“类名.变量名“，“类名.方法名”的方式。

