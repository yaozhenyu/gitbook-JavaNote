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



