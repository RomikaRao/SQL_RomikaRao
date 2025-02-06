# SQL_Practice

show databases;
create database VIT;
drop database vit;

use vit;
create table CSE(
s_id int,
s_name varchar(30),
s_mark int
);

drop table cse;
show tables from vit;
select * from cse;
insert into cse values(1001, 'Ram Prasad', 99);
insert into cse values(1002, 'Riya', 95);
insert into cse values(1003, 'Rahul', 80);
insert into cse values(1004, 'Aliya', 85);
insert into cse values(1005, 'Pihu', 80,'uk');

ALTER TABLE cse ADD(
    address VARCHAR(200)
);

desc cse;
Alter table cse drop column address;
alter table cse add (s_country varchar(25) default 'India');

update cse set s_name ='Vishnu' where s_id=1002;
update cse set s_mark = s_mark+1;

create database practice1;
use practice1;
create table Mech(s_id int,s_name varchar(25));
START TRANSACTION;
insert into Mech values (101,'jayanth');
savepoint A;
update mech set s_id = 102 where s_id = 101;
savepoint B;
insert into  mech values(103,'Kartik');
select * from mech;

CREATE DATABASE ORG123;
SHOW DATABASES;
USE ORG123;

CREATE TABLE Workers (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);

desc workers;

INSERT INTO Workers 
	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
		(001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),
		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),
		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),
		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),
		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),
		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),
		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),
		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');
select * from workers;

SELECT * FROM Workers WHERE SALARY > 100000 AND DEPARTMENT = 'HR';

select salary from workers where salary between 100000 and 200000;

select first_name from workers where worker_id =2 or worker_id=4;

select * from workers where salary between 200000 and 400000 and worker_id not in (1,2,3,4,5);

SELECT min(salary)
FROM workers
WHERE Department = 'HR';

SELECT FIRST_NAME, LAST_NAME  FROM Worker  
WHERE DEPARTMENT = 'HR'  
AND SALARY = (SELECT MIN(SALARY) FROM Worker WHERE DEPARTMENT = 'HR');

Select max(salary), min(salary) from workers where department='Account';

#SELECT COUNT(column_name)
#FROM table_name
#WHERE condition;

#SELECT AVG(column_name)
#FROM table_name
#WHERE condition;

#SELECT SUM(column_name)
#FROM table_name
#WHERE condition;

select * from workers;
select distinct(department) from workers;

#alias - Giving some temporary name to a column name
select worker_id as emp_Code from worker;

select worker_id from workers union select worker_id from worker;

select worker_id from workers union all select worker_id from worker;

select worker_id from workers union select first_name from worker;

SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;

SELECT s_id, s_name FROM cse
WHERE s_id=1002
UNION
SELECT s_id, s_name FROM mech
WHERE s_id=101
ORDER BY s_id;

SELECT DEPARTMENT, WORKER_ID 
FROM Worker 
WHERE DEPARTMENT = 'HR' 

UNION 

SELECT DEPARTMENT, WORKER_ID 
FROM Worker 
WHERE DEPARTMENT = 'Account';

SELECT worker_id, first_name,department,
CASE
    WHEN salary > 300000 THEN 'Rich people'
    WHEN salary <=300000 && salary >=100000 THEN 'Middle stage'
    ELSE 'Poor people'
END 
AS People_stage_wise
FROM worker;

select*from worker where department='Admin' order by department;
select*from worker where department='Admin' order by salary desc limit 3;

select department, count(department) as total_employees from workers 
where department='HR' or department='Account' group by department;

select department, count(department) as total_employees from worker
group by department
order by total_employees desc;

create table Persons(
ID int primary key,
LastName varchar(255) not null unique,
FirstName varchar(255) not null unique,
Age int);

desc persons;


