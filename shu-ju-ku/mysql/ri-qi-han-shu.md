# 日期函数

**常用**

_**获取系统当前日期**_

```
SELECT CURDATE()
SELECT CURRENT_DATE()
-> 2016-01-16
-> 2016-01-16
```

_**获取系统当前时间**_

```
SELECT CURTIME()
SELECT CURRENT_TIME()
-> 17:44:22
-> 17:44:22
```

_**NOW\(\)，SYSDATE\(\)，CURRENT\_TIMESTAMP\(\)，LOCALTIME\(\)：获取系统当前日期和时间**_

```
SELECT NOW()
SELECT SYSDATE()
SELECT CURRENT_TIMESTAMP()
SELECT CURRENT_TIMESTAMP
SELECT LOCALTIME()
SELECT LOCALTIME
-> 2016-01-16 17:44:41
-> 2016-01-16 17:44:41
-> 2016-01-16 17:44:41
-> 2016-01-16 17:44:41
-> 2016-01-16 17:44:41
-> 2016-01-16 17:44:41
```

_**PERIOD\_ADD\(month，add\)**_

```
SELECT PERIOD_ADD(1601,2)
SELECT PERIOD_ADD(191602,3)
SELECT PERIOD_ADD(191602,-3)
该函数返回对month做增减的操作结果，month的格式为yyMM或者yyyyMM,返回的都是yyyyMM格式的结果，add可以传负值
```

_**PERIOD\_DIFF\(monthStart，monthEnd\)**_

```
SELECT PERIOD_DIFF(1601,1603)
SELECT PERIOD_DIFF(191602,191607)
SELECT PERIOD_DIFF(1916-02,1916-07)
SELECT PERIOD_DIFF(1602,9002)
该函数返回monthStart - monthEnd的间隔月数
```

_**DATE\_ADD\(date，INTERVAL number type\)，同 ADDDATE\(\)**_

```
SELECT DATE_ADD("2015-12-31 23:59:59",INTERVAL 1 SECOND)
SELECT DATE_ADD("2015-12-31 23:59:59",INTERVAL 1 DAY)
SELECT DATE_ADD("2015-12-31 23:59:59",INTERVAL "1:1" MINUTE_SECOND)
SELECT DATE_ADD("2016-01-01 00:00:00",INTERVAL "-1 10" DAY_HOUR)

DATE_ADD()和ADDDATE()返回对date操作的结果
1、date的格式可以是"15-12-31"，可以是"15-12-31 23:59:59",也可以是"2015-12-31 23:59:59"，
如果参数date是date格式，则返回date格式结果，如果参数date是datetime格式，则返回datetime格式结果
2、type格式：
SECOND 秒 SECONDS
MINUTE 分钟 MINUTES
HOUR 时间 HOURS
DAY 天 DAYS
MONTH 月 MONTHS
YEAR 年 YEARS
MINUTE_SECOND 分钟和秒 "MINUTES:SECONDS"
HOUR_MINUTE 小时和分钟 "HOURS:MINUTES"
DAY_HOUR 天和小时 "DAYS HOURS"
YEAR_MONTH 年和月 "YEARS-MONTHS"
HOUR_SECOND 小时, 分钟， "HOURS:MINUTES:SECONDS"
DAY_MINUTE 天, 小时, 分钟 "DAYS HOURS:MINUTES"
DAY_SECOND 天, 小时, 分钟, 秒 "DAYS HOURS:MINUTES:SECONDS"
3、另外，如果不用函数，也可以考虑用操作符"+"，"-"，例子如下：
SELECT "2016-01-01" - INTERVAL 1 SECOND
SELECT "2016-01-01" - INTERVAL 1 DAY
SELECT '2016-12-31 23:59:59' + INTERVAL 1 SECOND
SELECT '2016-12-31 23:59:59' + INTERVAL "1:1" MINUTE_SECOND
返回结果：
-> 2015-12-31 23:59:59
-> 2015-12-31
-> 2017-01-01 00:00:00
-> 2017-01-01 00:01:00
```

_**DATE\_SUB\(date，INTERVAL number type\)，同 SUBDATE\(\)**_

用法和DATE\_ADD\(\)与ADDDATE\(\)类似，一个是加，一个是减

_**DATE\_FORMAT\(date，format\)：根据参数对date进行格式化。**_

```
SELECT DATE_FORMAT('2016-01-16 22:23:00','%W %M %Y')
SELECT DATE_FORMAT('2016-01-16 22:23:00','%D %y %a %d %m %b %j')
SELECT DATE_FORMAT('2016-01-16 22:23:00','%H %k %I %r %T %S %w')
SELECT DATE_FORMAT('2016-01-16 22:23:00','%Y-%m-%d %H:%i:%s')
-> Saturday January 2016
-> 16th 16 Sat 16 01 Jan 016
-> 22 22 10 10:23:00 PM 22:23:00 00 6
-> 2016-01-16 22:23:00
format的格式都列出来：
%M 月名字(January……December)
%W 星期名字(Sunday……Saturday)
%D 有英语前缀的月份的日期(1st, 2nd, 3rd, 等等。）
%Y 年, 数字, 4 位
%y 年, 数字, 2 位
%a 缩写的星期名字(Sun……Sat)
%d 月份中的天数, 数字(00……31)
%e 月份中的天数, 数字(0……31)
%m 月, 数字(01……12)
%c 月, 数字(1……12)
%b 缩写的月份名字(Jan……Dec)
%j 一年中的天数(001……366)
%H 小时(00……23)
%k 小时(0……23)
%h 小时(01……12)
%I 小时(01……12)
%l 小时(1……12)
%i 分钟, 数字(00……59)
%r 时间,12 小时(hh:mm:ss [AP]M)
%T 时间,24 小时(hh:mm:ss)
%S 秒(00……59)
%s 秒(00……59)
%p AM或PM
%w 一个星期中的天数(0=Sunday ……6=Saturday ）
%U 星期(0……52), 这里星期天是星期的第一天
%u 星期(0……52), 这里星期一是星期的第一天
%% 字符% )
TIME_FORMAT(time,format)：
具体用法和DATE_FORMAT()类似,但TIME_FORMAT只处理小时、分钟和秒(其余符号产生一个NULL值或0)
```

_**UNIX\_TIMESTAMP（date）：获取时间戳**_

```
SELECT UNIX_TIMESTAMP()
SELECT UNIX_TIMESTAMP('2016-01-16')
SELECT UNIX_TIMESTAMP('2016-01-16 23:59:59')
-> 1452937627
-> 1452873600
-> 1452959999
```

**其他**

**1、DAYOFWEEK\(date\)**

```
SELECT DAYOFWEEK('2016-01-16')
SELECT DAYOFWEEK('2016-01-16 00:00:00')(表示：星期天=1，星期一=2， ... 星期六=7)
```

**2、WEEKDAY\(date\)**

```
SELECT WEEKDAY('2016-01-16')
SELECT WEEKDAY('2016-01-16 00:00:00')
0=星期一，1=星期二， ... 5=星期六
```

**3、DAYOFMONTH\(date\)**

```
SELECT DAYOFMONTH('2016-01-16')
SELECT DAYOFMONTH('2016-01-16 00:00:00')
当月的第几天，1号就返回1，... ,31号就返回31
```

**4、DAYOFYEAR\(date\)**

```
SELECT DAYOFYEAR('2016-03-31')
SELECT DAYOFYEAR('2016-03-31 00:00:00')
(表示返回date是当年的第几天，01.01返回1，... ,12.31就返回365)
```

**5、MONTH\(date\)**

```
SELECT MONTH('2016-01-16')
SELECT MONTH('2016-01-16 00:00:00')(表示返回date是当年的第几月，1月就返回1，... ,12月就返回12)
```

**6、DAYNAME\(date\)**

```
SELECT DAYNAME('2016-01-16')
SELECT DAYNAME('2016-01-16 00:00:00')
(表示返回date是周几的英文全称名字)
```

**7、MONTHNAME\(date**\)

```
SELECT MONTHNAME('2016-01-16')
SELECT MONTHNAME('2016-01-16 00:00:00')
(表示返回date的是当年第几月的英文名字)
```

**8、QUARTER\(date\)**

```
SELECT QUARTER('2016-01-16')
SELECT QUARTER('2016-01-16 00:00:00')(表示返回date的是当年的第几个季度，返回1,2,3,4)
```

**9、WEEK\(date，index\)**

```
SELECT WEEK('2016-01-03')
SELECT WEEK('2016-01-03', 0)
SELECT WEEK('2016-01-03', 1)
(该函数返回date在一年当中的第几周，date(01.03)是周日，默认是以为周日作为一周的第一天，
函数在此处返回1可以有两种理解：1、第一周返回0，第二周返回1，.... ,2、以当年的完整周开始计数，第一周返回1，第二周返回2，... ，
最后一周返回53)
(week()默认index就是0. 所以结果同上)(当index为1时，表示一周的第一天是周一，所以，4号周一才是第二周的开始日)
```

**10、YEAR\(date\)**

```
SELECT YEAR('70-01-16')
SELECT YEAR('2070-01-16')
SELECT YEAR('69-01-16 00:00:00')(表示返回date的4位数年份)
要注意的是：如果年份只有两位数，那么自动补全的机制是以默认时间1970.01.01为界限的，>= 70 的补全 19，< 70 的补全 20
```

**11、HOUR\(time\)**

```
SELECT HOUR('11:22:33')
SELECT HOUR('2016-01-16 11:22:33')
返回该date或者time的hour值，值范围（0-23）
```

**12、MINUTE\(time\)**

```
SELECT MINUTE('11:22:33')
SELECT MINUTE('2016-01-16 11:44:33')
返回该time的minute值，值范围（0-59）
```

**13、SECOND\(time\)**

```
SELECT SECOND('11:22:33')
SELECT SECOND('2016-01-16 11:44:22')
返回该time的minute值，值范围（0-59）
```

**14、TO\_DAYS\(date\)**

```
SELECT TO_DAYS('2016-01-16')
SELECT TO_DAYS('20160116')
SELECT TO_DAYS('160116')
-> 736344
-> 736344
-> 736344
返回西元0年至日期date是总共多少天
```

**15、FROM\_DAYS\(dat**e\)

```
SELECT FROM_DAYS(367)
-> 0001-01-02
返回西元0年至今多少天的DATE值
```

16**、FROM\_UNIXTIME\(unix\_timestamp,format\)：把时间戳转化成日期时间**

```
SELECT FROM_UNIXTIME(1452959999)
SELECT FROM_UNIXTIME(1452959999,'%Y-%m-%d %H:%i:%s')
-> 2016-01-16 23:59:59
-> 2016-01-16 23:59:59
```

17**、SEC\_TO\_TIME\(seconds\)：把秒数转化成时间**

```
SELECT SEC_TO_TIME(2378)
-> 00:39:38
```

18**、TIME\_TO\_SEC\(time\)：把时间转化成秒数**

```
SELECT TIME_TO_SEC('22:23:00')
-> 2378
```

19**、ADDTIME\(time，times\)：把times加到time上**

`SELECT ADDTIME("2015-12-31 23:59:59",'01:01:01')`

`-> 2016-01-01 01:01:00`

20**、CONVERT\_TZ\(date,from\_tz ,to\_tz \)：转换时区**

```
SELECT CONVERT_TZ('2004-01-01 12:00:00','+00:00','+10:00')
-> 2004-01-01 22:00:00
```

21**、STR\_TO\_DATE\(date，format \)：将字符串转成format格式的日期时间**

```
SELECT STR_TO_DATE('2015-01-01', '%Y-%m-%d')
-> 2015-01-01
```

22**、LAST\_DAY\(date \)：获取date当月最后一天的日期**

```
SELECT LAST_DAY(SYSDATE())
SELECT LAST_DAY('2015-02-02')
SELECT LAST_DAY('2015-02-02 00:22:33')
-> 2016-01-31
-> 2015-02-28
-> 2015-02-28
```

23**、MAKEDATE\(year ,dayofyear \)：根据参数（年份，第多少天）获取日期**

```
SELECT MAKEDATE(2015 ,32)
-> 2015-02-01
```

24**、 MAKETIME\(hour ,minute ,second \)：根据参数（时，分，秒）获取时**间

```
SELECT MAKETIME(12 ,23 ,34 )
-> 12:23:34
```

25**、YEARWEEK\(date\)：获取日期的年和周**

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



