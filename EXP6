create table emps(
    employee_id int primary key,
    last_name varchar(50),
    salary decimal(10,2),
    department_id int,
    hir_date date,
    job_id varchar(50),
    comission decimal(10,2),
    manager_id int
);
INSERT INTO employees VALUES (101, 'Smith', 15000, 20, '05-02-1992', 'SA_REP', 500.00, 102);
INSERT INTO employees VALUES (102, 'Allen', 9000, 50, '1994-06-20', 'ST_CLERK', NULL, NULL);
INSERT INTO employees VALUES (103, 'Clark', 12000, 20, '1998-02-25', 'SA_REP', 1000.00, 102);
INSERT INTO employees VALUES (104, 'Adams', 4000, 10, '1994-12-01', 'ST_CLERK', NULL, 103);
INSERT INTO employees VALUES (105, 'Baker', 5000, 20, '1998-01-05', 'SA_REP', 600.00, 103);
INSERT INTO emps VALUES (106, 'Adam', 4000, 176, '09-12-1992', 'ST_CLERK', NULL, 103);
INSERT INTO emps VALUES (177, 'Adul', 4000, 10, '04-11-1998', 'ST_CLERK', NULL, 103);

select last_name,salary from emps where salary>12000;

select last_name,department_id from emps where employee_id=176;

select last_name,salary from emps where salary not between 5000 and 12000;

select last_name,department_id from emps where hir_date between('02-20-1998') and ('05-01-1998') order by hir_date asc;

select last_name,department_id from emps where department_id in(20,50) order by last_name asc;
select last_name as employee,salary as monthly_salary from emps where salary between 5000 and 12000 and department_id in(20,50) order by last_name asc;
select last_name,hir_date from emps where to_char(hir_date,'YYYY') ='1994';
select last_name,job_id from emps where manager_id is null;
select last_name,salary,comission from emps where comission is not null order by salary desc,comission desc;
SELECT last_name FROM emps WHERE last_name LIKE '__a%';
SELECT last_name FROM emps WHERE last_name LIKE '%a%' AND last_name LIKE '%e%';
SELECT last_name, job_id, salary FROM emps WHERE job_id IN ('SA_REP', 'ST_CLERK') AND salary NOT IN (2500, 3500, 7000);
