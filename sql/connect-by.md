# Connect by

```
select ... start with initial-condition connect by nocycle recurse-condition

select ... connect by recurse-condition

select ... start with initial-condition connect by nocycle recurse-condition

select ... connect by recurse-condition
```

oracle 实例

```
set feedback off

create table test_connect_by (
  parent     number,
  child      number,
  constraint uq_tcb unique (child)
);


```



