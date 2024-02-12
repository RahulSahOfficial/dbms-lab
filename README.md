# DBMS LAB
---
## EXPERIMENT – 1
---
Problem 1.1 - Create a table called EMP with the following structure.
Name Type
-------------------------------- -------------------------
EMPNO NUMBER(6)
ENAME VARCHAR2(20)
JOB VARCHAR2(10)
MGR NUMBER(4)
DEPTNO NUMBER(3)
SAL NUMBER(7,2)
Allow NULL for all columns except ename and job.


```sql
create table emp(
empno number(6),
ename varchar2(20) not null,
job varchar2(20) not null,
mgr number(3),
deptno number(3),
sal number(7,2));
```


Problem 1.2 - Add a column commission to the emp table Commission numeric null allowed.
```sql
alter table emp add commission number(7);
```
Problem 1.3 - Modify the column width of the job field of Emp table
```sql
alter table emp modify job varchar2(20);
```

Problem 1.4 - Create dept table with the following structure.
DEPTNO NUMBER(2)
DNAME VARCHAR2(10)
LOC VARCHAR2(10)
Deptno as the primary key
```sql
 create table dept(deptno number(2) primary key,dname varchar2(10),loc varchar2(10));

```
Problem 1.5 - Add constraints to the emp table that empno as the primary key and deptno as
the foreign key.
```sql
alter table emp add constraint PK_EMP primary key(empno);
alter table emp add constraint FK_EMP_DEPT_DEPTNO foreign key (deptno) references dept(deptno);

```

Problem 1.6 - Add constraints to the emp table to check the empno value while entering (i.e)
empno > 100.
```sql
alter table emp add constraint EMPNOGT1000 check(empno>100);

```


Problem 1.7 - Salary value by default is 5000, otherwise as entered values
```sql
alter table emp modify sal default 5000;
```


Problem 1.8 - Add columns Dob to the emp table.
```sql
alter table emp add dob date;
```

---
EXPERIMENT – 2
---
Problem 2.1 - Insert 3 records into dept table
```sql
insert into dept values(10,'Development','Hyderabad');
insert into dept values(20,'Development','Hyderabad');
insert into dept values(30,'Administration','London');
```
output
```
    DEPTNO DNAME           LOC
---------- --------------- ----------
        10 Maintenance     Banglore
        20 Development     Hyderabad
        30 Administration  London
```

Problem 2.2 - Insert 10 records into emp table.
```sql
insert into emp(empno,ename,job,deptno,sal,commission,dob)
values(7595,'Rahul Sah','CEO',30,40000,4000,'12-JUL-01');

insert into emp(empno,ename,job,mgr,deptno,sal,dob) 
values(7499,'Altaf Hussain','Manager',7595,30,35000,'15-OCT-02');

insert into emp(empno,ename,job,mgr,deptno,sal,dob,commission) \
values(7566,'Manish Choudhary','Manager',7595,30,25000,'13-DEC-02',2000);

insert into emp(empno,ename,job,mgr,deptno,sal,dob) 
values(7611,'Akash Goutam','Manager',7595,30,45000,'12-OCT-01');

insert into emp(empno,ename,job,mgr,deptno,sal,dob,commission) 
values(7758,'Sourav Sah','Manager',7595,30,55000,'9-APR-02',6000);

insert into emp(empno,ename,job,mgr,deptno,sal,dob,commission) 
values(7500,'Megha','Software Developer',7499,20,23000,'13-NOV-02',1500);

SQL> insert into emp(empno,ename,job,mgr,deptno,sal,dob,commission) 
values(7501,'Bajrang Yadav','Software Tester',7499,10,26000,'26-SEP-01',1550);

SQL> insert into emp(empno,ename,job,mgr,deptno,sal,dob) 
values(7567,'Chandan Pandit','Software Developer',7566,20,28000,'7-MAR-01');

insert into emp(empno,ename,job,mgr,deptno,sal,dob) 
values(7568,'Vishal Yadav','Software Tester',7566,10,18000,'17-OCT-01');

insert into emp(empno,ename,job,mgr,deptno,sal,dob,commission) 
values(7759,'Sahil Sah','System Tester',7758,10,33000,'13-JUL-02',2500);
```
Output
```

     EMPNO ENAME                JOB                         MGR     DEPTNO        SAL COMMISSION DOB
---------- -------------------- -------------------- ---------- ---------- ---------- ---------- ---------
      7595 Rahul Sah            CEO                                     30      40000       4000 12-JUL-01
      7499 Altaf Hussain        Manager                    7595         30      35000            15-OCT-02
      7566 Manish Choudhary     Manager                    7595         30      25000       2000 13-DEC-02
      7611 Akash Goutam         Manager                    7595         30      45000            12-OCT-01
      7758 Sourav Sah           Manager                    7595         30      55000       6000 09-APR-02
      7500 Megha                Software Developer         7499         20      23000       1500 13-NOV-02
      7501 Bajrang Yadav        Software Tester            7499         10      26000       1550 26-SEP-01
      7567 Chandan Pandit       Software Developer         7566         20      28000            07-MAR-01
      7568 Vishal Yadav         Software Tester            7566         10      18000            17-OCT-01
      7759 Sahil Sah            System Tester              7758         10      33000       2500 13-JUL-02

10 rows selected.
```

Problem 2.3 - Update the emp table to set the default commission of all employees to Rs
1000/- who are working as managers
```sql
update emp set commission=1000 where job='Manager';
```

Problem 2.4 - Create a pseudo table employee with the same structure as the table emp and
insert rows into the table using select clauses
```sql
create table employee as select * from emp;
```

Problem 2.5 - Delete only those who are working as supervisors.
```sql
insert into employee(empno,ename,job,mgr,deptno,sal,dob,commission) 
values(7612,'Rohit Gupta','Supervisor',7611,20,15000,'13-OCT-02',500);

delete from employee where job='Supervisor';
```

Problem 2.6 - Delete the rows whose empno is 7599
```sql
delete from employee where empno=7599;
```

Problem 2.7 - List the records in the emp table orderby salary in ascending order.
```sql
select * from emp order by sal;
```

Problem 2.8 - List the records in the emp table orderby salary in descending order.
```sql
select * from emp order by sal desc;
```

Problem 2.9 - Display only those employees whose deptno is 30
```sql
select * from emp where deptno=30;
```

Problem 2.10 - Display deptno from the table employee avoiding the duplicated values.
```sql
select distinct(deptno) from emp;
```

Problem 2.11 - List the records in sorted order of their employees.
```sql
select * from emp order by ename;
```

Problem 2.12 - Create a manager table from the emp table which should hold details only
about the managers.
```sql
create table manager as select * from emp where job='Manager';
```

Problem 2.13 - List the employee names whose commission is null.
```sql
select * from emp where commission is null;
```

Problem 2.14 - List the employee names and the department name in which they are working.
```sql
select ename,dname from emp 
inner join dept 
on emp.deptno=dept.deptno;
```

---
Experiment 3:
---

Problem 3.1 - Select all employees from the departments “Maintenance” and “development”
```sql
select * from emp
inner join dept
on emp.deptno=dept.deptno 
where dname='Maintenance' OR dname='Development';
```

Problem 3.2 - Display all the details of the records whose employee names start
with ‘S’.
```sql
select * from emp where ename like 'S%';
```

Problem 3.3 - Display all the details of the records whose employee name does
not start with ‘S’.
```sql
select * from emp where ename not like 'S%';
```

Problem 3.4 - Display the rows whose empno ranges from 7500 to 7600.
```sql
select * from emp where empno between 7500 and 7600;
```

Problem 3.5 - Display the rows whose empno not in range from 7500 to7600.
```sql
select * from emp where empno not between 7500 and 7600;
```

Problem 3.6 - Calculate the square root of the salary of all employees.
```sql
select empno,ename,sqrt(sal) from emp;
```

Problem 3.7 - Count the total records in the emp table.
```sql
select count(*) total_records from emp;
```

Problem 3.8 - Calculate the total and average salary amount of the emp table.
```sql
select sum(sal) total_salary,avg(sal) average_salary from emp;
```

Problem 3.9 - Determine the max and min salary and display as max_salary and min_salary.
```sql
select max(sal) max_salary,min(sal) min_salary from emp;
```

Problem 3.10 - Display total salary spent for employees.
```sql
select sum(sal) total_salary_spent from emp;
```

Problem 3.11 - Display total salary spent for each job category.
```sql
select job,sum(sal) total_salary_spent from emp group by job;
```

Problem 3.12 - Display the month name of date “14-jul-09” in full.
```sql
select to_char(to_date('14-JUL-09'), 'Month') month from dual;
```

Problem 3.13 - Display the Dob of all employees in the format “dd-mm-yy”.
```sql
select empno,ename,to_char(dob,'dd-mm-yy') dob from emp;
```

Problem 3.14 - Display the date two months after the Dob of employees.
```sql
select empno,ename,add_months(dob,2) new_dob from emp;
```

Problem 3.15 - Display the last date of that month in “05-Oct-09”.
```sql
select last_day(to_date('05-Oct-09')) last_day from dual;
```

Problem 3.16 - Display the rounded date in the year format, month format,day format in the employees.
```sql
select empno,ename,dob,round(dob,'YEAR') round_year,round(dob,'month') round_month,round(dob,'day') round_day from emp;
```

Problem 3.17 - List all employee names , salary and 15% rise in salary.
```sql
select ename,sal*1.15 new_sal from emp;
```

Problem 3.18 - List all employee names which start with either B or C.
```sql
select * from emp where ename like 'B%' OR ename like 'C%';
```

Problem 3.19-Display the employee names who got less than the average salary of all
employees.
```sql
select * from emp where sal<(select avg(sal) from emp);
```

Problem 3.20 - Display lowest paid employee details under each manager.
```sql
select mgr,min(sal) min_sal from emp group by mgr;
```

Problem 3.21 - Display number of employees working in each department and their department name.
```sql
select d.dname,count(*) no_of_emp from dept d left outer join emp e on d.deptno=e.deptno group by d.deptno,d.dname;
```

Problem 3.22 - Display the employee names whose name contains up to 5characters.
```sql
select ename from emp where length(ename)<=5;
```

Problem 3.23 - List all employee names and their manager whose
manager is 77499 or 7566 0r 7611.
```sql
select ename,mgr from emp where mgr in (7499,7566,7611);
```

Problem 3.24 - Find how many job titles are available in employee table.
```sql
select count(distinct(job)) no_of_jobs_titles from emp;
```

Problem 3.25 -What isthe difference between maximum and minimum salaries of employeesin the organization?
```sql
select max(sal)-min(sal) diff from emp;
```

Problem 3.26 - Find no.of depts in employee table.
```sql
 select count(distinct(deptno)) no_of_dept from emp;
```

Problem 3.27 - Display the names and dob of all employees who were born in February.
```sql
select ename,dob from emp where to_char(dob,'mm')='02';
```

Problem 3.28 - List out the employee names who will celebrate their birth days during current month.
```sql
select ename,dob from emp where to_char(dob,'mm')=(select to_char(sysdate,'mm') from dual);
```

Problem 3.29 - List out the employee names whose names starts with s and ends with h.
```sql
select ename from emp where ename like 'S%h';
```

Problem 3.30 - List out the employee names whose salary is greater than 5000.
```sql
select * from emp where sal>5000;
```
