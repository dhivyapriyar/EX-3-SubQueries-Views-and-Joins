# EX 3 SubQueries, Views and Joins 


## Create employee Table
```
sql
create table emp (empno int(10) primary key,name char(30),job char(30),sal int(10),deptno int(8));
```
## Insert the values
```
sql
insert into emp(empno,name,job,sal,deptno) values (1201,'dhivya','manager',1235,12);

insert into emp(empno,name,job,sal,deptno) values (1202,'varsha','clerk',1234,13);

insert into emp(empno,name,job,sal,deptno) values (1203,'swetha','manager',12345,15);

insert into emp(empno,name,job,sal,deptno) values (1204,'vidhya','clerk',1236,12);

insert into emp(empno,name,job,sal,deptno) values (1205,'prabha','salesman',1237,13);

insert into emp(empno,name,job,sal,deptno) values (1206,'jeeva','accountant',12345,17);

```

## Create department table
```
sql
create table dept(deptno int(5) primary key,deptname char(30),loc char(40));
```
## Insert the values in the department table
```
sql
insert into dept (deptno,deptname,loc) values (1,'research','chandigarh');

insert into dept (deptno,deptname,loc) values (2,'accounting','delhi');

insert into dept (deptno,deptname,loc) values (3,'manufacture','chennai');

insert into dept (deptno,deptname,loc) values (4,'marketing','hyderabad');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
```
create view minimum as select name,job,sal from emp where sal =(select min(sal) from emp);
```

### OUTPUT:
![3 1](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/548c9137-42ee-46bd-beaa-544a0380cf6a)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
```
CREATE VIEW minimum AS select ENAME,JOB,SAL from EMP where SAL =(select MIN(SAL) from EMP);
```

### OUTPUT:
![3 2](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/c20d4cb8-b2ba-4eb3-a0e2-90e49a258b6b)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```
 select name,job from emp where  deptno=12 and job='manager';
```

### OUTPUT:
![3 3](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/ad51c325-172f-4e41-a9a8-2713911585e2)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```
create view empv5 as select empno,name,job from emp where deptno=13;
```

### OUTPUT:
![3 4](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/a68a54bb-b200-4839-a036-96caa19c68b8)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```
 create view empv30 as select empno,name,sal from emp where deptno=17;
```

### OUTPUT:
![3 5](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/cc8477e9-d25a-4ea7-97dc-5977545cfd1e)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```
 update emp set sal=sal*1.1 where job='clerk';
```

### OUTPUT:
![3 6](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/2eb5d9d8-87ff-4a47-9054-ed6431fba051)

## Create a Customer1 Table
```
sql
create table customer1(cusid int(8),cusname char(20),city char(92),grade int(5),salesid int(27));
```
## Inserting Values to the Table
```
sql
insert into customer1 (cusid,cusname,city,grade,salesid) values (100,'dhivya','chennai',5,123);

insert into customer1 (cusid,cusname,city,grade,salesid) values (102,'varsha','chennai',5,123);

insert into customer1 (cusid,cusname,city,grade,salesid) values (103,'vidhya','kanchipuram',5,125);

insert into customer1 (cusid,cusname,city,grade,salesid) values (104,'yuva','coimbatore',7,126);

insert into customer1 (cusid,cusname,city,grade,salesid) values (108,'prabha','kerala',4,127);
```
## Create a Salesperson1 table
```
sql
create table salesperson (salesid int(2),city char(39),salesname char(20),commission int(5));
```
## Inserting Values to the Table
```
sql
insert into salesperson(salesid,city,salesname,commission) values(1,'chennai','vijis',100);

insert into salesperson(salesid,city,salesname,commission) values(2,'puzhal','dhru',500);

insert into salesperson(salesid,city,salesname,commission) values(3,'pondy','jeeva',400);

insert into salesperson(salesid,city,salesname,commission) values(4,'nungambakkam','deepesh',700);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```
select salesperson.salesname AS "Salesman", customer1.cusname as "Customer Name", salesperson.city AS "City" from salesperson inner join customer1 on salesperson.city=customer1.city;
```

### OUTPUT:
![3 7](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/869e87c8-679f-4f61-b37b-c136101820de)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```
select customer1.cusname as "Customer Name",customer1.city as "Customer City",salesperson.salesname AS "Salesman",salesperson.commission as "Commission" from salesperson inner join customer1 on salesperson.salesid=customer1.salesid where salesperson.commission>400;
```

### OUTPUT:
![3 8](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/0a923143-155d-4a39-a88a-b2fc35f40e09)

### Q9) Perform Natural join on both tables

### QUERY:
```
 select customer1.cusname as "Customer Name",customer1.city as "Customer City",salesperson.salesname AS "Salesman",salesperson.commission as "Commission" from salesperson inner join customer1 on salesperson.salesid=customer1.salesid where salesperson.commission>400;
```


### OUTPUT:
![3 9](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/d19b410f-3a93-444e-afca-2ecd05b4d68c)

### Q10) Perform Left and right join on both tables

### QUERY FOR LEFT JOIN:
```
select * from salesperson left join customer1 on salesperson.city=customer1.city;
```

### OUTPUT:
![3 10](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/41dacc66-518d-4f4d-aece-0965d357f9d0)

### QUERY FOR RIGHT JOIN:
```
select * from salesperson RIGHT JOIN customer1 on salesperson.city=customer1.city;
```
### OUTPUT:
![3 11](https://github.com/dhivyapriyar/EX-3-SubQueries-Views-and-Joins/assets/119477552/65726b6b-0776-4961-adaa-7a9fbada98c3)

