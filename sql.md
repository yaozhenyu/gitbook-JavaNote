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



