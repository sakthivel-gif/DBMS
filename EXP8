CREATE TABLE employees_2 (
    employee_id   NUMBER PRIMARY KEY,
    last_name     VARCHAR2(50),
    job_id        VARCHAR2(20),
    manager_id    NUMBER,
    hire_date     DATE,
    salary        NUMBER,
    commission_pct NUMBER,
    department_id NUMBER
);

CREATE TABLE departments_2 (
    department_id   NUMBER PRIMARY KEY,
    department_name VARCHAR2(50),
    location_id     NUMBER
);

CREATE TABLE locations (
    location_id NUMBER PRIMARY KEY,
    city  VARCHAR2(50)
);

CREATE TABLE job_grades_1 (
    grade_level VARCHAR2(2),
    lowest_sal  NUMBER,
    highest_sal NUMBER
);

INSERT INTO locations VALUES (1000, 'New York');
INSERT INTO locations VALUES (1400, 'Toronto');
INSERT INTO locations VALUES (1700, 'Sydney');

INSERT INTO departments_2 VALUES (10, 'Administration', 1000);
INSERT INTO departments_2 VALUES (20, 'IT', 1400);
INSERT INTO departments_2 VALUES (80, 'Sales', 1700);

INSERT INTO employees_2 VALUES (101, 'King', 'AD_PRES', NULL, DATE '2003-06-17', 24000, NULL, 10);
INSERT INTO employees_2 VALUES (102, 'Smith', 'IT_PROG', 101, DATE '2005-01-15', 6000, NULL, 20);
INSERT INTO employees_2 VALUES (103, 'Matos', 'SA_REP', 102, DATE '2006-03-10', 5000, 0.15, 80);
INSERT INTO employees_2 VALUES (104, 'Davies', 'SA_REP', 102, DATE '2004-08-01', 4800, 0.10, 80);

INSERT INTO job_grades_1 VALUES ('A', 1000, 2999);
INSERT INTO job_grades_1 VALUES ('B', 3000, 5999);
INSERT INTO job_grades_1 VALUES ('C', 6000, 9999);
INSERT INTO job_grades_1 VALUES ('D', 10000, 24000);

Select e.last_name,e.department_id,d.department_name from employees_2 e
join departments_2 d on e.department_id=d.department_id

SELECT DISTINCT e.job_id, d.location_id, l.city
FROM employees_2 e
JOIN departments_2 d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
WHERE e.department_id = 80;

SELECT e.last_name, d.department_name, d.location_id, l.city
FROM employees_2 e
JOIN departments_2 d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
WHERE e.commission_pct IS NOT NULL;

SELECT e.last_name, d.department_name
FROM employees_2 e
JOIN departments_2 d ON e.department_id = d.department_id
WHERE LOWER(e.last_name) LIKE '%a%';

SELECT e.last_name, e.job_id, e.department_id, d.department_name
FROM employees_2 e
JOIN departments_2 d ON e.department_id = d.department_id
JOIN locations l ON d.location_id = l.location_id
WHERE l.city = 'Toronto';

SELECT e.last_name AS Employee, e.employee_id AS Emp#,
       m.last_name AS Manager, m.employee_id AS Mgr#
FROM employees_2 e
LEFT JOIN employees_2 m ON e.manager_id = m.employee_id;

SELECT e.last_name AS Employee, e.employee_id AS Emp#,
       m.last_name AS Manager, m.employee_id AS Mgr#
FROM employees_2 e
JOIN employees_2 m ON e.manager_id = m.employee_id
ORDER BY e.employee_id;

SELECT e1.last_name AS Employee,
       e1.department_id AS Dept#,
       e2.last_name AS Colleague
FROM employees_2 e1
JOIN employees_2 e2
     ON e1.department_id = e2.department_id
WHERE e1.last_name <> e2.last_name;

DESC job_grades_1;

SELECT e.last_name,
       e.job_id,
       d.department_name,
       e.salary,
       j.grade_level
FROM employees_2 e
JOIN departments_2 d
    ON e.department_id = d.department_id
JOIN job_grades_1 j
    ON e.salary BETWEEN j.lowest_sal AND j.highest_sal;

SELECT last_name, hire_date
FROM employees_2
WHERE hire_date > (
      SELECT hire_date
      FROM employees_2
      WHERE last_name = 'Davies');

 Select e.last_name as Employee,e.hire_date as "Emp Hired",
    m.last_name As Manager,m.hire_date as "Mgr Hired"
from employees_2 e
join employees_2 m on e.manager_id = m.employee_id
where e.hire_date<m.hire_date
