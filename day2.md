# 存储过程

__概念：__   
为了处理流程，业务而存在的，创建的存储过程会自动保存到数据库中，启动数据库时，会自动加载到内存中
1. 有输入参数，输出参数，输入输出参数
2. 存储过程只能在plsql代码块中调用，不能在sql语句中调用
3. 没有返回值
   

__语法：__
```sql
create or replace procedure 存储过程名[(参数名 [in|out|in out] 类型名 [default 默认值])]
is
  --声明部分
begin
  --代码块
  --异常处理部分
end;  
```

__关键字：__  
```sql
procedure ：存储过程关键字  
in :输入参数，默认为输入参数  
out:输出参数  
in out:输入输出参数  
```
## 调用方法  

1.代码块中调用，不需要传参时  
```sql
declare
begin
存储过程名[()];
end;
```
2.代码块中调用，需要传参时
```sql
 declare
 begin
 存储过程名();
 end;
```
3.代码块中  
```sql
call 存储过程名();
```
4.命令行中  
```sql
exec 存储过程名();
```
__--创建存储过程__  
```sql
 create or replace procedure p1
 is
 begin
 dbms_output.put_line('测试存储过程');
 end;
```
__--调用存储过程__
```sql
begin
  p1;
end;  

begin
  p1();
end;
call p1();
exec p1(); 只能在控制台使用
```
## 参数

### in  
输入参数，只能使用参数值，不能修改参数内容，只读参数，可以使用任何方式进行传参  

__传参方式：__
1. 传值  
2. 传变量 
3. 参数名=>值  

__例题__ --写一个存储过程，在存储过程中根据传进去的员工编号，打印员工信息;  
```sql
create or replace procedure p1(eno in number)  --eno为实际参数
is
--声明变量，保存emp表中的一条记录
  v emp%rowtype;
begin
  select * into v from emp where empno = eno; 
  dbms_output.put_line(v.empno||','||v.ename||','||v.job||','||v.sal||','||v.deptno);
end;

--调用
declare
  a number:=&a; --a为形式参数
begin
  p1(a);
end;
```
### out  
输出参数，输出参数，参数值可修改，一般输入时参数的值无任何意义，将存储过程的处理结果传给外部程序只能用传变量的方式传参

__例题__--根据传入的员工编号，给调用程序传出员工信息  
```sql
create or replace procedure p1(eno in number,v out emp%rowtype)
is

begin
  select * into v from emp where empno = eno;
end;

  --调用
declare
  v emp%rowtype;
begin
  p1(7369,v);
  dbms_output.put_line(v.empno||','||v.ename||','||v.job||','||v.mgr||','||v.hiredate||','||v.sal||','||v.comm||','||v.deptno);
  v.ename:='peiqi';
end;
```
### in out  
in out参数：输入输出参数，它结合了输入参数和输出参数的特点，在存储过程中可以修改参数值，必须以传变量的方式传参

__例题__
1. --根据传入的员工编号，给调用程序传出员工信息  
```sql 
create or replace procedure p1(v in out emp%rowtype)
is
begin
v.empno:=7788;
select * into v from emp where empno = v.empno;
end;
--调用
declare
    v emp%rowtype;
begin
    v.empno:=7369;
    p1(v);
    dbms_output.put_line(v.empno||','||v.ename||','||v.job||','||v.sal||','||v.deptno);
end;
```

2. --传入一个部门编号，查询出部门中的员工信息  
```sql 
create or replace procedure p1(dno number,cur out    
sys_refcursor)
is

begin
open cur for select * from emp where deptno = dno;
end;
```

### 调用
```sql
declare
  --定义系统游标类型，接收存储过程传出的数据
  cur sys_refcursor;
  --声明变量，保存游标中的一条数据
  v emp%rowtype;
begin
  p1(10,cur);
  --循环遍历
  loop
    --遍历游标
    fetch cur into v;
    --退出循环
    exit when cur%notfound;
    --循环体
    dbms_output.put_line(v.empno||','||v.ename||','||v.job||','||v.hiredate||','||v.sal||','||v.deptno);
  end loop;
  close cur;
end;
```

__--例题__  使用存储过程，打印9*9乘法表  
```sql
create or replace procedure p1
is

begin
  for i in 1..9 loop
    for j in 1..i loop
      dbms_output.put(j||'*'||i||'='||i*j||' ');
      if i*j < 10 then
        dbms_output.put(' ');
      end if;
    end loop;
    dbms_output.put_line('');
  end loop;
end;

call p1();
```
__--怎么查看存储过程的代码__
```sql
select * from user_source where name = 'P1';
```
