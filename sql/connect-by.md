## **Oracle中start with…connect by prior子句用法**

```
select ... from tablename 
    start with cond1 
    connect by cond2 
    where cond3;
```

COND1

是根结点的限定语句，当然可以放宽限定条件，以取得多个

根结点，实际就是多棵树。





COND2

是连接条件，其中用

PRIOR

表示上一条记录，比如



CONNECT BY PRIOR ID=PRAENTID

就是说上一条记录的

ID

是本

条记录的

PRAENTID

，即本记录的父亲是上一条记录。





COND3

是过滤条件，用于对返回的所有记录进行过滤

。





Oracle 

的树形查找语句

connect by prior ... start with... 





2 

Start with 

后面跟的是开始结点即从什么位置开始查找。可以有多个

起始结点



,Connect by





连接有父子关系的两个节点



id = parent\_id 

怎么去遍历这棵树

prior

是关键

,

如果

prior 

在

parent\_id 

这一侧

（

id=prior parent\_id

）则说明向父节点查找即自底向上查找，如果

prior

在

id 

这一侧（

prior id= parent\_id

）则说明向子结点方向查找即

自顶向下查找

oracle 实例

```
set feedback off

create table test_connect_by (
  parent     number,
  child      number,
  constraint uq_tcb unique (child)
);

-- 5=2+3
insert into test_connect_by values ( 5, 2);
insert into test_connect_by values ( 5, 3);

-- 18=11+7
insert into test_connect_by values (18,11);
insert into test_connect_by values (18, 7);

-- 17 = 9+8 
insert into test_connect_by values (17, 9);
insert into test_connect_by values (17, 8);

-- 26 = 13+1+12 
insert into test_connect_by values (26,13);
insert into test_connect_by values (26, 1);
insert into test_connect_by values (26,12);

-- 15=10+5
insert into test_connect_by values (15,10);
insert into test_connect_by values (15, 5);


-- 38=15+17+6
insert into test_connect_by values (38,15);
insert into test_connect_by values (38,17);
insert into test_connect_by values (38, 6);

-- 38, 26 and 18 have no parents (the parent is null) 
insert into test_connect_by values (null, 38);
insert into test_connect_by values (null, 26);
insert into test_connect_by values (null, 18);

select lpad(' ',2*(level-1)) || to_char(child) s 
  from test_connect_by 
  start with parent is null
  connect by prior child = parent;

This select statement results in:  
38
  15
    10
    5
      2
      3
  17
    9
    8
  6
26
  13
  1
  12
18
  11
  7
```



