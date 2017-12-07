# 结构化查询语言

**SQL\( Structured Query Language\)**

## 解锁\(oracle\)

### 1.下面的语句用来查询哪些对象被锁：

```
select object_name,machine,s.sid,s.serial# 
from v$locked_object l,dba_objects o ,v$session s 
where l.object_id　=　o.object_id and l.session_id=s.sid;
```

### 2.下面的语句用来杀死一个进程：

```
alter system kill session '24,111';
//(其中24,111分别是上面查询出的sid,serial#)
```

# Oracle

获取表：

```
select table_name from user_tables; //当前用户拥有的表      
select table_name from all_tables; //所有用户的表 
select table_name from dba_tables; //包括系统表
```

获取表注释：

```
select * from user_tab_comments
```

获取字段注释：

```
select * from user_col_comments
```



