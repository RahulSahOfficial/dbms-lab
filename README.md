EXPERIMENT – 1 date: 6/feb/2024
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


EXPERIMENT – 2 date: 6/feb/2024
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


Experiment 3:


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
---

## Experiment 04
---

Creating Tables
```sql
create table dept080 (deptno number(3),dname varchar2(20),loc varchar2(20),primary key (deptno));
```
```sql
create table emp080 (empno number(5),ename varchar2(20), job varchar2(20), hiredate date,mgr number(5),sal number(7,2),comm number(7,2),deptno number(5),primary key(empno),constraint FK_EMP080DEPT080_DEPTNO foreign key (deptno) references dept080);
```
```sql
insert into dept080 values(10,'Accounting','New York');
insert into dept080 values(20,'Research','Dallas');
insert into dept080 values(30,'Sales','Chicago');
insert into dept080 values(40,'Operations','Boston');
```
```sql
insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7369,'Smith','Clerk','17-DEC-80',7902,800,20);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,comm,deptno) 
values(7499,'Allen','Salesman','20-FEB-81',7698,1600,300,30);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,comm,deptno) 
values(7521,'Ward','Salesman','22-FEB-81',7698,1250,500,30);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7566,'Jones','Manager','2-APR-81',7839,2975,20);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,comm,deptno) 
values(7654,'Martin','Salesman','28-SEP-81',7698,1250,1400,30);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7698,'Blake','Manager','1-MAY-81',7839,2850,30);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7782,'Clark','Manager','9-JUN-81',7839,2450,10);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7788,'Scott','Analyst','19-APR-87',7566,3000,20);

insert into emp080 (empno,ename,job,hiredate,sal,deptno) 
values(7839,'King','President','17-NOV-81',5000,20);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,comm,deptno) 
values(7844,'Turner','Salesman','8-SEP-81',7698,1500,0,30);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7876,'Adams','Clerk','23-May-87',7788,1100,20);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7900,'James','Clerk','3-Dec-81',7698,950,30);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7902,'Ford','Analyst','3-Dec-81',7566,3000,20);

insert into emp080 (empno,ename,job,hiredate,mgr,sal,deptno) 
values(7934,'Miller','Clerk','23-Jan-82',7782,1300,10);
```

Output
---
1. Emp080 Table
```
     EMPNO ENAME                JOB                  HIREDATE         MGR        SAL       COMM     DEPTNO
---------- -------------------- -------------------- --------- ---------- ---------- ---------- ----------
      7369 Smith                Clerk                17-DEC-80       7902        800                    20
      7499 Allen                Salesman             20-FEB-81       7698       1600        300         30
      7521 Ward                 Salesman             22-FEB-81       7698       1250        500         30
      7566 Jones                Manager              02-APR-81       7839       2975                    20
      7654 Martin               Salesman             28-SEP-81       7698       1250       1400         30
      7698 Blake                Manager              01-MAY-81       7839       2850                    30
      7782 Clark                Manager              09-JUN-81       7839       2450                    10
      7788 Scott                Analyst              19-APR-87       7566       3000                    20
      7839 King                 President            17-NOV-81                  5000                    20
      7844 Turner               Salesman             08-SEP-81       7698       1500          0         30
      7876 Adams                Clerk                23-MAY-87       7788       1100                    20
      7900 James                Clerk                03-DEC-81       7698        950                    30
      7902 Ford                 Analyst              03-DEC-81       7566       3000                    20
      7934 Miller               Clerk                23-JAN-82       7782       1300                    10
```
2. Dept080 Table
```
    DEPTNO DNAME                LOC
---------- -------------------- --------------------
        10 Accounting           New York
        20 Research             Dallas
        30 Sales                Chicago
        40 Operations           Boston
```

Problem 4.1 : Select all employees from 'Accounting' and 'Sales' dept.
```sql
select * from emp080 where deptno in (select deptno from dept080 where dname in ('Accounting','Sales'));
```

Problem 4.2 : Display all employee names and salary whose salary is greater than minimum salary of the company and job title starts with ‘M’.

```sql
select ename,sal from emp080 where sal>(select min(sal) from emp080) and job like 'M%';
```

Problem 4.3 : Issue a query to find all the employees who work in the same job as jones.
```sql
select * from emp080 where job=(select job from emp080 where ename='Jones');
```

Problem 4.4 : Issue a query to display information about employees who earn more thanany employee in dept 30.
```sql
select * from emp080 where sal>(select min(sal) from emp080 where deptno=30);
```

Problem 4.5 : Display the employees who have the same job as jones and whose salary >= fords.
```sql
 select * from emp080 where job=(select job from emp080 where ename='Jones') AND sal>=(select sal from emp080 where ename='Ford');
```

Problem 4.6 : Write a query to display the name and job of all employees in Sales dept.
```sql
select ename,job from emp080 where deptno=(select deptno from dept080 where dname='Sales');
```

Problem 4.7 : Issue a query to list all the employees who salary is > the average salary oftheir own dept.
```sql
select * from emp080 e1 where sal>(select avg(sal) from emp080 e2 where e2.deptno = e1.deptno);
```

Problem 4.8 : Write a query that would display the empname, job, location and the name of their dept.
```sql
select ename,job,loc,dname from emp080 inner join dept080 on emp080.deptno=dept080.deptno;
```

Problem 4.9 : Write a query to list the employees having the same job as employeeslocated in 'New York'.(use multiple subquery)
```sql
select * from emp080 where job in(select job from emp080 where deptno =(select deptno from dept080 where loc='New York'));
```

Problem 4.10 : Write a query to list the employees in dept 10 with the same job asanyone in the Research dept
```sql
select * from emp080 
where deptno=10 AND job in 
(
    select distinct(job) from emp080 
    inner join dept080 
    on emp080.deptno=dept080.deptno where dname='Research'
);
```

Problem 4.11: Write a query to list the employees with the same job and salary as
‘ford’.
```sql
select * from emp080 
where (job,sal) 
in (select job,sal from emp080 where ename = 'Ford');
```

Problem 4.12: Write a query to list all depts. with at least 2 salesman.
```sql
select e.deptno,d.dname,count(*) as no_of_salesman 
from emp080 e 
inner join dept080 d 
on e.deptno=d.deptno 
where e.job='Salesman' 
group by e.deptno,d.dname 
having count(*)>=2;
```

Problem 4.13: Write a query to list the employees in dept 20 with the same job asanyone in dept 30.
```sql
select * from emp080 
where deptno=20 and 
job in (select distinct(job) from emp080 where deptno=30);
```

Problem 4.14: List out the employee names who get the salary greater than themaximum
salaries of dept with dept no 20,30.
```sql
select ename from emp080 where sal>(select max(sal) from emp080 where deptno in(20,30));
```

Problem 4.15: Display the maximum salaries of the departments whose maximumsalary is greater than 9000.
```sql
select deptno,max(sal) from emp080 where sal>9000 group by deptno;
```

Problem 4.16: Display the maximum salaries of the departments whose minimumsalary is greater than 1000 and lesser than 5000.
```sql
select deptno,max(sal) from emp080
group by deptno 
having min(sal)>1000 and min(sal)<5000;
```

For exercises  4.17 and 4.18 Create one table named Accredit with columns deptno (foreign key of
department table),Rank varchar(20)
Problem 4.17: Display the department names that are accredited by the quality council.
```sql

```


Problem 4.18: Display the employees of departments which are not accredited by thequality council
```sql

```

Problem 4.19: Display all the employees and the departments implementing a left
outer join.
```sql
select * from dept080 
left outer join emp080 
on dept080.deptno=emp080.deptno;
```

Problem 4.20: Display the employee name and department name in which they are working
implementing a right outer join.
```sql
select ename,dname from emp080 right outer join dept080 on emp080.deptno=dept080.deptno;
```

Problem 4.21: Display the employee name and department name in which they areworking
implementing a full outer join.
```sql
select * from emp080 full outer join dept080 on emp080.deptno=dept080.deptno;
```

Problem 4.22: Write a query to display their employee names and their managersname.
```sql
select e1.ename employee,e2.ename manager 
from emp080 e1 
inner join emp080 e2 on e1.mgr=e2.empno;
```

Problem 4.23: Write a query to display their employee names and their managers salaryfor every employee.
```sql
select e1.ename employee,e2.sal manager_sal 
from emp080 e1 
inner join emp080 e2 
on e1.mgr=e2.empno;
```

Problem 4.24: Write a query to output the name , job, empno, deptname and locationfor each dept, even if there are no employees.
```sql
select ename,job,empno,dname,loc 
from emp080 
right outer join dept080 
on emp080.deptno=dept080.deptno;
```

Problem 4.25: Find the name of the manager for each employee. Include the followingin the output:
empno, empname, job and his manager’s name.
```sql
select e1.empno,e1.ename,e1.job,e2.ename manager 
from emp080 e1 
inner join emp080 e2 
on e1.mgr=e2.empno;
```

Problem 4.26: Display the details of those who draw the same salary.
```sql
select e1.ename employee1_name,e1.sal employee1_sal,e2.ename employee2_name,e2.sal employee2_sal from emp080 e1 inner join emp080 e2 on e1.sal=e2.sal and e1.empno!=e2.empno;
```
