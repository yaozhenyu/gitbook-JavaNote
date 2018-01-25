# 常用SQL

1、显示两个日期之间的所有月份

```
SELECT TO_CHAR(ADD_MONTHS(TO_DATE('2016-08', 'YYYY-MM'), ROWNUM - 1),
               'YYYY-MM') sdate
  FROM DUAL
CONNECT BY ROWNUM <=
           months_between(sysdate, to_date('2016-08', 'yyyy-mm')) + 1
```

2、显示两个日期之间的所有日期

```
SELECT
    TO_CHAR( TO_DATE( '2018-01-19', 'yyyy-mm-dd' )+ LEVEL - 1, 'yyyy-mm-dd' ) AS sdate
FROM
    dual
CONNECT BY
    LEVEL <= TO_DATE( '2018-01-19', 'yyyy-mm-dd' ) - TO_DATE( '2018-01-01', 'yyyy-mm-dd' )+ 1
```

3、oracle行转列

```
SELECT
	*
FROM
	(
		SELECT
			SUBSTR( al.putoutdate, 1, 7 ) sdate,
			TO_CHAR( TO_DATE( aps.FINISHDATE, 'yyyy-MM-dd' ), 'yyyy-MM' ) fi,
			SUM( aps.PAYPRINCIPALAMT )/ 10000 su
		FROM
			account_loan al,
			ACCOUNT_PAYMENT_SCHEDULE aps
		WHERE
			al.id = aps.accountno
			AND al.LOANSTATUS = '3'
			AND aps.PAYTYPE = '5'
		GROUP BY
			SUBSTR( al.putoutdate, 1, 7 ),
			TO_CHAR( TO_DATE( aps.FINISHDATE, 'yyyy-MM-dd' ), 'yyyy-MM' )
		ORDER BY
			sdate,
			fi
	) pivot(
		MAX( su ) FOR fi IN(
			'2016-08' AS "2016-08",
			'2016-09' AS "2016-09",
			'2016-10' AS "2016-10",
			'2016-11' AS "2016-11",
			'2016-12' AS "2016-12",
			'2017-01' AS "2017-01",
			'2017-02' AS "2017-02",
			'2017-03' AS "2017-03",
			'2017-04' AS "2017-04",
			'2017-05' AS "2017-05",
			'2017-06' AS "2017-06",
			'2017-07' AS "2017-07",
			'2017-08' AS "2017-08",
			'2017-09' AS "2017-09",
			'2017-10' AS "2017-10",
			'2017-11' AS "2017-11",
			'2017-12' AS "2017-12",
			'2018-01' AS "2018-01"
		)
	)
```



