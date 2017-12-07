## 1.下面的语句用来查询哪些对象被锁：

```
select object_name,machine,s.sid,s.serial# 
from v$locked_object l,dba_objects o ,v$session s 
where l.object_id　=　o.object_id and l.session_id=s.sid;
```

2.下面的语句用来杀死一个进程：

alter system kill session '24,111';



