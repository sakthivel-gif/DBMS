CREATE OR REPLACE VIEW EMPLOYEE_VU AS
SELECT 
    EMPLOYEE_NUMBER,
    EMPLOYEE_NAME AS EMPLOYEE,
    DEPARTMENT_NUMBER
FROM EMPLOYEES;

SELECT * FROM EMPLOYEE_VU;

SELECT view_name, text
FROM user_views;

SELECT EMPLOYEE, department_id
FROM EMPLOYEE_VU;

SELECT EMPLOYEE, department_id AS DEPARTMENT
FROM EMPLOYEE_VU;

CREATE OR REPLACE VIEW DEPT50 AS
SELECT
    employee_id AS EMPNO,
    last_name AS EMPLOYEE,
    department_id AS DEPTNO
FROM EMPLOYEES
WHERE department_id = 50
WITH CHECK OPTION;

DESC DEPT50;
or
SELECT column_name, data_type, data_length
FROM user_tab_columns
WHERE table_name = 'DEPT50';
or
SELECT * FROM DEPT50;

UPDATE DEPT50
SET DEPTNO = 80
WHERE EMPLOYEE = 'Matos';

CREATE OR REPLACE VIEW SALARY_VU AS
SELECT
    e.last_name AS Employee,
    d.department_name AS Department,
    e.salary AS Salary,
    j.grade AS Grade
FROM EMPLOYEES e
JOIN DEPARTMENTS d ON e.department_id = d.department_id
JOIN JOB_GRADE j ON e.salary BETWEEN j.lowest_sal AND j.highest_sal;
