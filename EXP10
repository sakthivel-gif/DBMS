CREATE TABLE employees_4 (
    employee_id    NUMBER PRIMARY KEY,
    first_name     VARCHAR2(20),
    last_name      VARCHAR2(20),
    job_id         VARCHAR2(10),
    manager_id     NUMBER,
    hire_date      DATE,
    salary         NUMBER,
    commission_pct NUMBER,
    department_id  NUMBER
);
CREATE TABLE departments_4 (
    department_id   NUMBER PRIMARY KEY,
    department_name VARCHAR2(30),
    location_id     NUMBER
);
CREATE TABLE locations_2(
    location_id NUMBER PRIMARY KEY,
    city        VARCHAR2(30)
);

INSERT INTO locations_2 VALUES (1000, 'New York');
INSERT INTO locations_2 VALUES (1100, 'London');
INSERT INTO locations_2 VALUES (1200, 'Tokyo');
INSERT INTO locations_2 VALUES (1300, 'Delhi');

INSERT INTO departments_4 VALUES (10, 'Administration', 1000);
INSERT INTO departments_4 VALUES (20, 'Marketing', 1100);
INSERT INTO departments_4 VALUES (50, 'Sales', 1200);
INSERT INTO departments_4 VALUES (80, 'Finance', 1300);
INSERT INTO departments_4 VALUES (90, 'IT', 1000);

INSERT INTO employees_4 VALUES (101, 'John', 'King', 'AD_PRES', NULL, DATE '1995-06-17', 24000, NULL, 90);
INSERT INTO employees_4 VALUES (102, 'Neena', 'Kochhar', 'AD_VP', 101, DATE '1996-09-21', 17000, NULL, 90);
INSERT INTO employees_4 VALUES (103, 'Lex', 'De Haan', 'AD_VP', 101, DATE '1997-01-13', 17000, NULL, 90);
INSERT INTO employees_4 VALUES (104, 'Alexander', 'Hunold', 'IT_PROG', 103, DATE '1998-01-03', 9000, NULL, 90);
INSERT INTO employees_4 VALUES (105, 'Bruce', 'Ernst', 'IT_PROG', 103, DATE '1998-05-21', 6000, NULL, 90);
INSERT INTO employees_4 VALUES (106, 'David', 'Austin', 'IT_PROG', 103, DATE '1997-06-25', 4800, NULL, 90);
INSERT INTO employees_4 VALUES (107, 'Valli', 'Pataballa', 'SA_REP', 102, DATE '1998-01-23', 8600, 0.2, 50);
INSERT INTO employees_4 VALUES (108, 'Diana', 'Lorentz', 'SA_REP', 102, DATE '1995-02-07', 7000, 0.15, 50);
INSERT INTO employees_4 VALUES (109, 'Nancy', 'Greenberg', 'FI_MGR', 101, DATE '1996-08-17', 12000, NULL, 80);
INSERT INTO employees_4 VALUES (110, 'Daniel', 'Faviet', 'FI_ACCOUNT', 109, DATE '1997-08-16', 9000, NULL, 80);
INSERT INTO employees_4 VALUES (111, 'John', 'Chen', 'FI_ACCOUNT', 109, DATE '1996-09-28', 8200, NULL, 80);
INSERT INTO employees_4 VALUES (112, 'Ismael', 'Sciarra', 'MK_REP', 102, DATE '1995-07-19', 6000, NULL, 20);
INSERT INTO employees_4 VALUES (113, 'Jose', 'Urman', 'MK_REP', 102, DATE '1998-03-07', 6500, NULL, 20);

SELECT
    ROUND(MAX(salary)) AS Maximum,
    ROUND(MIN(salary)) AS Minimum,
    ROUND(SUM(salary)) AS Sum,
    ROUND(AVG(salary)) AS Average
FROM employees_4;
SELECT
    job_id,
    ROUND(MIN(salary)) AS Minimum,
    ROUND(MAX(salary)) AS Maximum,
    ROUND(SUM(salary)) AS Sum,
    ROUND(AVG(salary)) AS Average
FROM employees_4
GROUP BY job_id;

SELECT job_id, COUNT(*) AS Num_of_People
FROM employees_4
WHERE job_id = 'FI_ACCOUNT'
GROUP BY job_id;

SELECT COUNT(DISTINCT manager_id) AS "Number of Managers"
FROM employees_4
WHERE manager_id IS NOT NULL;

SELECT (MAX(salary) - MIN(salary)) AS Difference
FROM employees_4;

SELECT manager_id, MIN(salary) AS Lowest_Salary
FROM employees_4
WHERE manager_id IS NOT NULL
GROUP BY manager_id
HAVING MIN(salary) > 6000
ORDER BY Lowest_Salary DESC;

SELECT
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN TO_CHAR(hire_date, 'YYYY') = '1995' THEN 1 ELSE 0 END) AS "Hired_1995",
    SUM(CASE WHEN TO_CHAR(hire_date, 'YYYY') = '1996' THEN 1 ELSE 0 END) AS "Hired_1996",
    SUM(CASE WHEN TO_CHAR(hire_date, 'YYYY') = '1997' THEN 1 ELSE 0 END) AS "Hired_1997",
    SUM(CASE WHEN TO_CHAR(hire_date, 'YYYY') = '1998' THEN 1 ELSE 0 END) AS "Hired_1998"
FROM employees_4;

SELECT job_id,
    SUM(CASE WHEN department_id = 20 THEN salary END) AS "Dept_20",
    SUM(CASE WHEN department_id = 50 THEN salary END) AS "Dept_50",
    SUM(CASE WHEN department_id = 80 THEN salary END) AS "Dept_80",
    SUM(CASE WHEN department_id = 90 THEN salary END) AS "Dept_90",
    SUM(salary) AS Total
FROM employees_4
WHERE department_id IN (20, 50, 80, 90)
GROUP BY job_id;

SELECT
    d.department_name || '-' || l.city AS "Name-Location",
    COUNT(e.employee_id) AS "Number of People",
    ROUND(AVG(e.salary), 2) AS "Salary"
FROM employees_4 e
JOIN departments_4 d ON e.department_id = d.department_id
JOIN locations_2 l ON d.location_id = l.location_id
GROUP BY d.department_name, l.city;
