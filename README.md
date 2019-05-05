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
    
    
    
    ---创建用户表
    create  table userinfo(
    userid  number(4) primary key,
    uname   varchar2(20)  not null,
    upwd    varchar2(10) 
    )
    --创建序列 自增
    create  sequence seq_userid 
    
    --
    create  trigger tri_userid
    before insert 
    on userinfo
    for each row 
    begin
    select seq_userid.nextval into :new.userid from  dual  
    end;
    
    
    
    ---插入数据
    insert into userinfo(uname,upwd) values('jack','');
    insert into userinfo(uname,upwd) values('tom','');
    insert into userinfo(uname,upwd) values('lily','');
    
    create or replace procedure pro_userreg(v_uname  userinfo.uname%type, v_upwd in userinfo.upwd%type)
    as 
    begin
    insert into userinfo(uname, upwd)  values(v_uname,v_upwd);
    end;
    
    
    
    
    
    declare
    v_uname userinfo.uname%type;
    v_upwd userinfo.uname%type;
    begin
    v_uname '&用户名'
    v_pwd '&密码';
    pro_userreg(v_uname,v_pwd);
    end;
    
     declare
    v_uname userinfo.uname%type;
    v_upwd userinfo.uname%type;
    begin
    v_uname '&用户名'
    v_pwd '&密码';
    pro_userreg(v_uname,v_pwd);
    end;
    
    
    
    
    
    
    
    
    
    
    
    
