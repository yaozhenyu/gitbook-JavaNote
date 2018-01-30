**常用日期函数**

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



