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

# 常用SQL

1、显示两个日期之间的所有月份\(递归connect by\)

```
SELECT TO_CHAR(ADD_MONTHS(TO_DATE('2016-08', 'YYYY-MM'), ROWNUM - 1),
               'YYYY-MM') sdate
  FROM DUAL
CONNECT BY ROWNUM <=
           months_between(sysdate, to_date('2016-08', 'yyyy-mm')) + 1
```

2、显示两个日期之间的所有日期\(递归connect by\)

```
SELECT
    TO_CHAR( TO_DATE( '2018-01-19', 'yyyy-mm-dd' )+ LEVEL - 1, 'yyyy-mm-dd' ) AS sdate
FROM
    dual
CONNECT BY
    LEVEL <= TO_DATE( '2018-01-19', 'yyyy-mm-dd' ) - TO_DATE( '2018-01-01', 'yyyy-mm-dd' )+ 1
```

3、oracle行转列 \(pivot\)

```
WITH tmp AS(
    SELECT
        '2018-01-01' AS date_,
        10 AS cost_am,
        20 AS cost_pm
    FROM
        dual
UNION ALL SELECT
        '2018-01-01' AS date_,
        13 AS cost_am,
        21 AS cost_pm
    FROM
        dual
UNION ALL SELECT
        '2018-01-02' AS date_,
        12 AS cost_am,
        25 AS cost_pm
    FROM
        dual
UNION ALL SELECT
        '2018-01-02' AS date_,
        11 AS cost_am,
        22 AS cost_pm
    FROM
        dual
UNION ALL SELECT
        '2018-01-03' AS date_,
        13 AS cost_am,
        24 AS cost_pm
    FROM
        dual
UNION ALL SELECT
        '2018-01-04' AS date_,
        15 AS cost_am,
        21 AS cost_pm
    FROM
        dual
UNION ALL SELECT
        '2018-01-04' AS date_,
        16 AS cost_am,
        29 AS cost_pm
    FROM
        dual
) SELECT
    *
FROM
    tmp pivot(
        SUM( cost_pm ) FOR date_ IN(
            '2018-01-01' AS "2018-01-01",
            '2018-01-02' AS "2018-01-02",
            '2018-01-03' AS "2018-01-03",
            '2018-01-04' AS "2018-01-04"
        )
    );
```

select \* from \(select a,b,c from tablename\) pivot \(max\(a\) for b in \('B1','B2','B3'\)\)

将b列，行转列，列名B1，B2，B3，行的值为max\(a\)，根据\('B1','B2','B3'\)值分组。



