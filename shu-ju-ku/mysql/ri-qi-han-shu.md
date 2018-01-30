# 日期函数

**DAYOFWEEK\(date\)**

```
SELECT DAYOFWEEK('2016-01-16')
SELECT DAYOFWEEK('2016-01-16 00:00:00')(表示：星期天=1，星期一=2， ... 星期六=7)
```

**WEEKDAY\(date\)**

```
SELECT WEEKDAY('2016-01-16')
SELECT WEEKDAY('2016-01-16 00:00:00')
0=星期一，1=星期二， ... 5=星期六
```

**DAYOFMONTH\(date\)**

```
SELECT DAYOFMONTH('2016-01-16')
SELECT DAYOFMONTH('2016-01-16 00:00:00')
当月的第几天，1号就返回1，... ,31号就返回31
```

**DAYOFYEAR\(date\)**

```
SELECT DAYOFYEAR('2016-03-31')
SELECT DAYOFYEAR('2016-03-31 00:00:00')
(表示返回date是当年的第几天，01.01返回1，... ,12.31就返回365)
```

**MONTH\(date\)**

```
SELECT MONTH('2016-01-16')
SELECT MONTH('2016-01-16 00:00:00')(表示返回date是当年的第几月，1月就返回1，... ,12月就返回12)
```

**DAYNAME\(date\)**

```
SELECT DAYNAME('2016-01-16')
SELECT DAYNAME('2016-01-16 00:00:00')
(表示返回date是周几的英文全称名字)
```

**MONTHNAME\(date**\)

```
SELECT MONTHNAME('2016-01-16')
SELECT MONTHNAME('2016-01-16 00:00:00')
(表示返回date的是当年第几月的英文名字)
```

**QUARTER\(date\)**

```
SELECT QUARTER('2016-01-16')
SELECT QUARTER('2016-01-16 00:00:00')(表示返回date的是当年的第几个季度，返回1,2,3,4)
```

**WEEK\(date，index\)**

```
SELECT WEEK('2016-01-03')
SELECT WEEK('2016-01-03', 0)
SELECT WEEK('2016-01-03', 1)
(该函数返回date在一年当中的第几周，date(01.03)是周日，默认是以为周日作为一周的第一天，
函数在此处返回1可以有两种理解：1、第一周返回0，第二周返回1，.... ,2、以当年的完整周开始计数，第一周返回1，第二周返回2，... ，
最后一周返回53)
(week()默认index就是0. 所以结果同上)(当index为1时，表示一周的第一天是周一，所以，4号周一才是第二周的开始日)
```

**YEAR\(date\)**

```
SELECT YEAR('70-01-16')
SELECT YEAR('2070-01-16')
SELECT YEAR('69-01-16 00:00:00')(表示返回date的4位数年份)
要注意的是：如果年份只有两位数，那么自动补全的机制是以默认时间1970.01.01为界限的，>= 70 的补全 19，< 70 的补全 20
```

**HOUR\(time\)**

```
SELECT HOUR('11:22:33')
SELECT HOUR('2016-01-16 11:22:33')
返回该date或者time的hour值，值范围（0-23）
```

**MINUTE\(time\)**

```
SELECT MINUTE('11:22:33')
SELECT MINUTE('2016-01-16 11:44:33')
返回该time的minute值，值范围（0-59）
```

**SECOND\(time\)**

```
SELECT SECOND('11:22:33')
SELECT SECOND('2016-01-16 11:44:22')
返回该time的minute值，值范围（0-59）
```

**TO\_DAYS\(date\)**

```
SELECT TO_DAYS('2016-01-16')
SELECT TO_DAYS('20160116')
SELECT TO_DAYS('160116')
-> 736344
-> 736344
-> 736344
返回西元0年至日期date是总共多少天
```

**FROM\_DAYS\(dat**e\)

```
SELECT FROM_DAYS(367)
-> 0001-01-02
返回西元0年至今多少天的DATE值
```

**FROM\_UNIXTIME\(unix\_timestamp,format\)：把时间戳转化成日期时间**

```
SELECT FROM_UNIXTIME(1452959999)
SELECT FROM_UNIXTIME(1452959999,'%Y-%m-%d %H:%i:%s')
-> 2016-01-16 23:59:59
-> 2016-01-16 23:59:59
```

**SEC\_TO\_TIME\(seconds\)：把秒数转化成时间**

```
SELECT SEC_TO_TIME(2378)
-> 00:39:38
```

**TIME\_TO\_SEC\(time\)：把时间转化成秒数**

```
SELECT TIME_TO_SEC('22:23:00')
-> 2378
```

**ADDTIME\(time，times\)：把times加到time上**

`SELECT ADDTIME("2015-12-31 23:59:59",'01:01:01')`

`-> 2016-01-01 01:01:00`

**CONVERT\_TZ\(date,from\_tz ,to\_tz \)：转换时区**

```
SELECT CONVERT_TZ('2004-01-01 12:00:00','+00:00','+10:00')
-> 2004-01-01 22:00:00
```

**STR\_TO\_DATE\(date，format \)：将字符串转成format格式的日期时间**

```
SELECT STR_TO_DATE('2015-01-01', '%Y-%m-%d')
-> 2015-01-01
```

**LAST\_DAY\(date \)：获取date当月最后一天的日期**

```
SELECT LAST_DAY(SYSDATE())
SELECT LAST_DAY('2015-02-02')
SELECT LAST_DAY('2015-02-02 00:22:33')
-> 2016-01-31
-> 2015-02-28
-> 2015-02-28
```

**MAKEDATE\(year ,dayofyear \)：根据参数（年份，第多少天）获取日期**

```
SELECT MAKEDATE(2015 ,32)
-> 2015-02-01
```

**MAKETIME\(hour ,minute ,second \)：根据参数（时，分，秒）获取时**间

```
SELECT MAKETIME(12 ,23 ,34 )
-> 12:23:34
```

**YEARWEEK\(date\)：获取日期的年和周**

```
SELECT YEARWEEK(SYSDATE())
SELECT YEARWEEK('2015-01-10')
SELECT YEARWEEK('2015-01-10',1)
-> 201602
-> 201501
-> 201502
35、WEEKOFYEAR(date)：获取当日是当年的第几周
SELECT WEEKOFYEAR(SYSDATE())
SELECT WEEKOFYEAR('2015-01-10')
-> 2
-> 2
```



