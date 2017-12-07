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

select
 * 
from
 user_col_comments
```



