## **Oracle中start with…connect by prior子句用法**

```
select ... from tablename 
    start with cond1 
    connect by cond2 
    where cond3;
```

COND1是根结点的限定语句，当然可以放宽限定条件，以取得多个根结点，实际就是多棵树。COND2是连接条件，其中用PRIOR表示上一条记录，比如CONNECT BY PRIOR ID=PRAENTID就是说上一条记录的ID是本条记录的PRAENTID，即本记录的父亲是上一条记。COND3是过滤条件，用于对返回的所有记录进行过滤。

oracle 实例

```
CREATE TABLE sys_menu AS
(SELECT '1' AS "id",'' AS "partentId" FROM dual UNION ALL
SELECT '2' AS "id",'1' AS "partentId" FROM dual UNION ALL
SELECT '3' AS "id",'2' AS "partentId" FROM dual UNION ALL
SELECT '4' AS "id",'3' AS "partentId" FROM dual UNION ALL
SELECT '5' AS "id",'2' AS "partentId" FROM dual UNION ALL
SELECT '6' AS "id",'5' AS "partentId" FROM dual UNION ALL
SELECT '7' AS "id",'6' AS "partentId" FROM dual UNION ALL
SELECT '8' AS "id",'7' AS "partentId" FROM dual UNION ALL
SELECT '9' AS "id",'8' AS "partentId" FROM dual UNION ALL
SELECT '10' AS "id",'9' AS "partentId" FROM dual
);

SELECT "id","partentId" FROM SYS_MENU
START WITH "id"='1'
CONNECT BY PRIOR "id"= "partentId";


```



