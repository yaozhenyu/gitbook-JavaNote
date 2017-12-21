# 常用SQL

1、显示两个日期之间的所有月份

```
SELECT TO_CHAR(ADD_MONTHS(TO_DATE('2016-08', 'YYYY-MM'), ROWNUM - 1),
               'YYYY-MM') yMonth
  FROM DUAL
CONNECT BY ROWNUM <=
           months_between(sysdate, to_date('2016-08', 'yyyy-mm')) + 1
```



