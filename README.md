# Oracle
---1.备份数据表
create table emp_bak as select * from  emp

---2.触发器
create trigger tri_delemp
after delete 
on emp_bak
for each row
  begin
    insert into
    emo_test(empno,ename,job,mgr,hiredate,sal,comn,deptno)
    values(:old.empno,:old.ename,:old.job,:old.mgr,:old.hiredate,:old.sal,:old.comm,:old.deptno);
    end;
