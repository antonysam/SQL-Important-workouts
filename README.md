# SQL-Important-workouts
## 1.Query to find Second Highest Salary of Employee?
```
Select min(salary) from (Select distinct salary from employees order by salary desc limit 2) result;

But there's a catch, this will return you only 1 column which is Salary, because in order to operate the distinction operation, DISTINCT can only operate on a specific set of columns. This means we should add another wrapping query to extract the employees(There can be multiple) that matches that result. Thus I added LIMIT 1 at the end.

The below query will provide all the details of the second largest salary employee
select * from employees where salary = (Select min(salary) from (Select distinct salary from employees order by salary desc limit 2) result) limit 1;
```
## 2.Query to find duplicate rows in table?
```
Select *,count(*)as duplicate from Cars1 group by company having duplicate > 1;
```
## 3.What is the Query to fetch first record from Cars1 table? 
```
select * from Cars1 where id = 1;
```
## 4.What is the Query to fetch last record from the table?
```
select * from Cars1 where id = (select max(id) from Cars1);
```
## 5.What is Query to display first 5 Records from Employee table?
```
select * from employees where employee_id limit 5;
```
## 6.What is Query to display last 5 Records from Employee table?
```
select * from employees order by employee_id desc limit 5;
```
## 7.How to get 3 Highest salaries records from Employee table?
```
select * from employees where salary = (select min(salary) from (select distinct salary from employees order by salary Desc limit 3)result) limit 1;
```
## 8.How to Display Odd rows in Employee table?
```
select * from employees where mod(employee_id,2)=1;
```
## 9.How to Display Even rows in Employee table?
```
select * from employees where mod(employee_id,2)=0;
```
## 10.How to fetch 3rd highest salary using dense_Rank Function?
```
select salary from (select dense_rank() over(order by salary desc)dense_rankSal,E.* from employees E) result where dense_rankSal = 3;

but if we need all details
select * from employees where salary = (select min(salary) from (select distinct salary from (select salary, dense_rank() over(order by salary desc)dense_rankSal from employees) result limit 3)result1);

```

```
