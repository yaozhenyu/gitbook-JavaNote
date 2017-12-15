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

导入类中的**静态方法或静态成员变量**，在引用类中可以直接使用，不用“类名.变量名“，“类名.方法名”的方式。

import static（静态导入）是JDK1.5中的新特性，一般我们导入一个类都用 import com.....ClassName;而静态导入是这样：import static com.....ClassName.\*;这里多了个static，还有就是类名ClassName后面多了个 .\* ，意思是导入这个类里的静态方法。当然，也可以只导入某个静态方法，只要把 .\* 换成静态方法名就行了。然后在这个类中，就可以直接用方法名调用静态方法，而不必用ClassName.方法名的方式来调用。



