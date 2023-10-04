# EX-3-SubQueries-Views-and-Joins
# Aim
To create views and joins in SQL

# Create employee Table
```sql
create table employee( emp_no numeric(4) primary key, job varchar(20),emp_name varchar(20),mgr numeric(4),hdate date,sal numeric(7,2),comm numeric(7,2),dept numeric(2));

```
# Insert the values
```sql
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7369,'Clerk','Hari',7902,'1980-12-17',800,null,20);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7499,'salesman','Ragav',7698,'1980-12-17',1600,300,20);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7521,'salesman','Paari',7698,'1980-12-17',1250,500,30);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7566,'manager','Chari',7839,'1980-12-17',2597,null,30);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7654,'salesman','Seenu',7698,'1980-12-17',1250,1400,10);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7698,'Manager','Theanu',7839,'1980-12-17',2850,null,20);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7782,'Manager','Venu',7839,'1980-12-17',2450,null,10);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7788,'Analyst','Baanu',7566,'1980-12-17',3000,null,20);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7839,'President','Joe',null,'1980-12-17',5000,null,10);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7876,'salesman','Josh',7698,'1980-12-17',1500,0,30);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7900,'Clerk','John',7902,'1980-12-17',1100,null,20);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7902,'Clerk','Jerry',7902,'1980-12-17',950,null,30);
insert into employee(emp_no,job,emp_name,mgr,hdate,sal,comm,dept) values (7934,'Analyst','Jay',7566,'1980-12-17',3000,10,20);
```
# Create department table
```sql
create table dept(dept_no numeric(2) primary key,dname varchar(20),loc varchar(20));
```
# Insert the values in the department table
```sql
Insert into dept (dept_no, dname, loc) VALUES (10, 'ACCOUNTING', 'NEW YORK');

Insert into dept (dept_no, dname, loc) VALUES (20, 'RESEARCH', 'DALLAS');

Insert into dept (dept_no, dname, loc) VALUES (30, 'SALES', 'CHICAGO');

Insert into dept (dept_no, dname, loc) VALUES (40, 'OPERATIONS', 'BOSTON');
```
# Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.

# QUERY:
```sql
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SALARY >(select SALARY from EMP where EMPNO=7566);
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/5a33552c-c387-4799-805c-de78094bae1a)


# Q2) List the ename,job,sal of the employee who get minimum salary in the company.

# QUERY:
```sql
CREATE VIEW minimum AS select emp_name,job,sal from employee where sal =(select MIN(sal) from employee);
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/1cca9a6d-0b91-4372-b81b-ccf106e56109)


# Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
# QUERY:
```sql
select emp_name,job from employee where  dept=10 AND job='salesman';
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/d512b219-5945-4221-9703-9e120dd88b49)


# Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.
# QUERY:
```sql
create view empv5 as select emp_no,emp_name,job from employee where dept=10;
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/c6058dd7-0cdb-4347-a2cd-697eee6de608)


# Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
# QUERY:
```sql
create view empv30 AS select emp_no,emp_name,sal from employee where dept=30;
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/863481eb-a9a1-4fac-9e80-465308e17a8a)


# Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
# QUERY:
```sql
update EMP set SALARY=SALARY*1.1 WHERE JOB='clerk';
create view empv6 as select emp_no,emp_name,job,sal from employee;
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/a9234f98-f882-4e6d-95f2-b188a05f0cdf)


# Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
# Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
# Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
# Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
# Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
# QUERY:
```sql
select s.name,c.cust_name,s.city from salesman1 as s ,customer1 as c where s.city=c.city;
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/3d5d944e-cb54-4103-89b3-842589414378)


# Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.
# QUERY:
```sql
select s.name,c.cust_name,c.city,s.commission from salesman1 as s inner join customer1 as c on s.city=c.city where s.commission>0.13;
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/bdf55cd9-6ca5-4fde-9214-73fa5313beda)


# Q9) Perform Natural join on both tables
# QUERY:
```sql
 select s.name,c.cust_name,c.city,s.commission from salesman1 as s natural join customer1 as c where s.commission>0.13;
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/f9846953-5f99-47f8-ae59-a4d91f760a06)


# Q10) Perform Left and right join on both tables
# QUERY:
```sql
select s.name,c.cust_name,c.city,s.commission from salesman1 as s left join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;

select s.name,c.cust_name,c.city,s.commission from salesman1 as s right join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;
```
# OUTPUT:
![image](https://github.com/Sabariakash22009103/EX-3-SubQueries-Views-and-Joins/assets/119390227/f3b7075b-05fd-4518-8dbe-2d78d18d38cb)



# RESULT:
Hence successfully created a manager database and executed views and joins using SQL.
