# 标量子查询

简单的理解就是写在select后面的子查询语句。比如：

```
select a.*,(select name from b where b.id=a.id) from a
```



