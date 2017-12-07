# 标量子查询

简单的理解就是写在select后面的子查询语句。比如：

```
select a.*,(select name from b where b.id=a.id) from a
```

理想状态下，a.id为主键，没有重复值，那么a表返回多少行，b表就要被执行多少次。

特殊情况下，a.id的distinct值只有n个，那么b表只执行n次。

如果a表数据比较多，标量子查询的效率非常低。

