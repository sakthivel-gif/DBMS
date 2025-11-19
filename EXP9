CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(50),
    location_id INT
);

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    last_name VARCHAR(50),
    job_id VARCHAR(20),
    manager_id INT,
    hire_date DATE,
    salary DECIMAL(10,2),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);

INSERT INTO departments VALUES (10, 'Administration', 1700);
INSERT INTO departments VALUES (20, 'Executive', 1700);
INSERT INTO departments VALUES (30, 'Sales', 1800);

INSERT INTO employees VALUES (101, 'King', 'AD_PRES', NULL, to_date('2003-06-17','yyyy-mm-dd'), 24000, 20);
INSERT INTO employees VALUES (102, 'Kochhar', 'AD_VP', 101, to_date('2005-09-21','yyyy-mm-dd'), 17000, 20);
INSERT INTO employees VALUES (102, 'Kochhar', 'AD_VP', 101, to_date('2005-09-21','yyyy-mm-dd'), 17000, 20);
INSERT INTO employees VALUES (103, 'De Haan', 'AD_VP', 101, to_date('2001-01-13','yyyy-mm-dd'), 17000, 20);
INSERT INTO employees VALUES (104, 'Zlotkey', 'SA_MAN', 100, to_date('2000-01-30','yyyy-mm-dd'), 10500, 30);
INSERT INTO employees VALUES (105, 'Abel', 'SA_REP', 104, to_date('2004-05-11','yyyy-mm-dd'), 11000, 30);
INSERT INTO employees VALUES (106, 'Taylor', 'SA_REP', 104, to_date('2004-06-15','yyyy-mm-dd'), 8600, 30);
INSERT INTO employees VALUES (107, 'Urman', 'IT_PROG', 103, to_date('2006-03-19','yyyy-mm-dd'), 9000, 10);
INSERT INTO employees VALUES (108, 'Grant', 'IT_PROG', 103, to_date('2007-01-23','yyyy-mm-dd'), 7000, 10);
INSERT INTO employees VALUES (109, 'Munoz', 'IT_PROG', 103, to_date('2008-02-15','yyyy-mm-dd'), 15000, 10);


SELECT last_name, hire_date
FROM employees
WHERE department_id = (
        SELECT department_id
        FROM employees
        WHERE last_name = 'Zlotkey'
    )
AND last_name <> 'Zlotkey';

SELECT employee_id, last_name, salary
FROM employees WHERE salary > (SELECT AVG(salary)FROM employees)ORDER BY salary ASC;

SELECT employee_id, last_name FROM employees WHERE department_id IN (SELECT DISTINCT department_id FROM employees WHERE last_name LIKE '%U%');

SELECT last_name, department_id, job_id FROM employees WHERE department_id IN (SELECT department_id FROM departments WHERE location_id = 1700);

SELECT last_name, salary FROM employees WHERE manager_id = (SELECT employee_id FROM employees WHERE last_name = 'King');

SELECT department_id, last_name, job_id FROM employees WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Executive');

SELECT employee_id, last_name, salary FROM employees WHERE salary > (SELECT AVG(salary)FROM employees)AND department_id IN (SELECT DISTINCT department_id FROM employees WHERE UPPER(last_name) LIKE '%U%');
