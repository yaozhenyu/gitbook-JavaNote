# Pl/Sql

```
DECLARE
v_num NUMBER ; -- 定义一个变量v_num
BEGIN
v_num := 30 ; -- 设置v_num的内容
DBMS_OUTPUT.put_line('V_NUM变量的内容是：' || v_num) ;
END ;
/
```

function

```
create or replace function fun_info(i_eno number,o_title out varchar2,salch in out number) return varchar2
as
name emp.ename%type;
begin
select ename into name from emp where empno=i_eno;
update emp set sal=sal+salch where empno=i_eno returning job,sal into o_title,salch;
return name;
end;
```



