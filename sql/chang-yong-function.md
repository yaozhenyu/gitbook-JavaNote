# 常用Function

```
--判断一个字符串是否是日期格式的函数
CREATE OR REPLACE FUNCTION is_date(parameter VARCHAR2) RETURN NUMBER IS
  val DATE;
BEGIN
  val := TO_DATE(NVL(parameter, 'a'), 'yyyy-mm-dd hh24:mi:ss');
  RETURN 1;
EXCEPTION
  WHEN OTHERS THEN
    RETURN 0;
END;
```



