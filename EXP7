-- Create tables

CREATE TABLE COUNTRIES (
    country_id VARCHAR(2) PRIMARY KEY,
    country_name VARCHAR(50)
);

CREATE TABLE DEPARTMENTS (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(50),
    country_id VARCHAR(2),
    FOREIGN KEY (country_id) REFERENCES COUNTRIES(country_id)
);

CREATE TABLE JOBS (
    job_id VARCHAR(10) PRIMARY KEY,
    job_title VARCHAR(50)
);

CREATE TABLE EMPLOYEES (
    employee_id INT PRIMARY KEY,
    last_name VARCHAR(50),
    job_id VARCHAR(10),
    department_id INT,
    original_job_id VARCHAR(10),
    FOREIGN KEY (job_id) REFERENCES JOBS(job_id),
    FOREIGN KEY (department_id) REFERENCES DEPARTMENTS(department_id),
    FOREIGN KEY (original_job_id) REFERENCES JOBS(job_id)
);

-- Insert sample data


SELECT department_id FROM DEPARTMENTS
MINUS
SELECT DISTINCT department_id FROM EMPLOYEES WHERE job_id = 'ST_CLERK';

SELECT country_id, country_name FROM COUNTRIES
MINUS
SELECT DISTINCT c.country_id, c.country_name
FROM COUNTRIES c
JOIN DEPARTMENTS d ON c.country_id = d.country_id;

-- Jobs for department 10
SELECT job_id, department_id FROM EMPLOYEES WHERE department_id = 10
UNION ALL
-- Jobs for department 50
SELECT job_id, department_id FROM EMPLOYEES WHERE department_id = 50
UNION ALL
-- Jobs for department 20
SELECT job_id, department_id FROM EMPLOYEES WHERE department_id = 20;

SELECT employee_id, job_id
FROM EMPLOYEES
WHERE job_id = original_job_id
AND employee_id IN (
    SELECT employee_id FROM EMPLOYEES GROUP BY employee_id HAVING COUNT(DISTINCT job_id) > 1
);

SELECT last_name, TO_CHAR(department_id) AS department_id_or_name
FROM EMPLOYEES

UNION ALL

SELECT NULL AS last_name, TO_CHAR(department_id) AS department_id_or_name
FROM DEPARTMENTS;
