-- (a) Find out the employee id, names, salaries of all the employees
SELECT Employee_id, First_Name, Last_Name, Salary FROM EMPLOYEES;

-- (b) List out the employees who work under manager 100
SELECT Employee_id, First_Name, Last_Name, Manager_id
FROM EMPLOYEES
WHERE Manager_id = 100;

-- (c) Find the names of the employees who have a salary greater than or equal to 4800
SELECT Employee_id, First_Name, Last_Name, Salary
FROM EMPLOYEES
WHERE Salary >= 4800;

-- (d) List out the employees whose last name is 'AUSTIN'
SELECT Employee_id, First_Name, Last_Name
FROM EMPLOYEES
WHERE UPPER(Last_Name) = 'AUSTIN';

-- (e) Find the names of the employees who work in departments 60, 70 and 80
SELECT Employee_id, First_Name, Last_Name, Department_id
FROM EMPLOYEES
WHERE Department_id IN (60, 70, 80);

-- (f) Display the unique Manager_Id
SELECT DISTINCT Manager_id FROM EMPLOYEES;
-- Create EMP table
CREATE TABLE EMP (
    EmpNo NUMBER(6),
    EmpName VARCHAR2(25),
    Job VARCHAR2(20),
    Basic NUMBER(8,2),
    DA NUMBER(8,2),
    HRA NUMBER(8,2),
    PF NUMBER(8,2),
    GrossPay NUMBER(10,2),
    NetPay NUMBER(10,2)
);

-- (a) Insert five records and calculate DA (30%), HRA (40%), PF (10%), GrossPay, NetPay
INSERT INTO EMP (EmpNo, EmpName, Job, Basic, DA, HRA, PF, GrossPay, NetPay)
VALUES (1, 'Ravi', 'Manager', 20000, 0.3*20000, 0.4*20000, 0.1*20000, (20000+0.3*20000+0.4*20000), (20000+0.3*20000+0.4*20000)-(0.1*20000));

INSERT INTO EMP VALUES (2, 'Kumar', 'Clerk', 12000, 0.3*12000, 0.4*12000, 0.1*12000, (12000+0.3*12000+0.4*12000), (12000+0.3*12000+0.4*12000)-(0.1*12000));
INSERT INTO EMP VALUES (3, 'Meena', 'Analyst', 18000, 0.3*18000, 0.4*18000, 0.1*18000, (18000+0.3*18000+0.4*18000), (18000+0.3*18000+0.4*18000)-(0.1*18000));
INSERT INTO EMP VALUES (4, 'Arun', 'Salesman', 15000, 0.3*15000, 0.4*15000, 0.1*15000, (15000+0.3*15000+0.4*15000), (15000+0.3*15000+0.4*15000)-(0.1*15000));
INSERT INTO EMP VALUES (5, 'Priya', 'HR', 25000, 0.3*25000, 0.4*25000, 0.1*25000, (25000+0.3*25000+0.4*25000), (25000+0.3*25000+0.4*25000)-(0.1*25000));

-- Display inserted data
SELECT * FROM EMP;

-- (b) Display employees whose Basic is the lowest (assuming department field existed)
-- Here we simply display the employee with the minimum Basic
SELECT * FROM EMP
WHERE Basic = (SELECT MIN(Basic) FROM EMP);

-- (c) If Net Pay is less than a certain value (e.g., 20000), display them
SELECT * FROM EMP
WHERE NetPay < 20000;
-- 1. Create DEPT table based on DEPARTMENT structure
CREATE TABLE DEPT (
    ID NUMBER(7) NOT NULL,
    NAME VARCHAR2(25) NOT NULL
);

-- 2. Create EMP table based on instance chart
CREATE TABLE EMP (
    ID NUMBER(7),
    LAST_NAME VARCHAR2(25),
    FIRST_NAME VARCHAR2(25),
    DEPT_ID NUMBER(7)
);

-- 3. Modify EMP table to allow longer last names (increase size to 50)
ALTER TABLE EMP MODIFY (LAST_NAME VARCHAR2(50));

-- 4. Create EMPLOYEES2 table based on EMPLOYEES structure (selected columns only)
CREATE TABLE EMPLOYEES2 AS
SELECT Employee_id AS Id,
       First_name,
       Last_name,
       Salary,
       Department_id AS Dept_id
FROM EMPLOYEES
WHERE 1=0;   -- copies structure only, no data

-- 5. Drop the EMP table
DROP TABLE EMP;

-- 6. Rename EMPLOYEES2 table as EMP
RENAME EMPLOYEES2 TO EMP;

-- 7. Add a comment on DEPT and EMP tables
COMMENT ON TABLE DEPT IS 'Department details table';
COMMENT ON TABLE EMP IS 'Employee details table';

-- Confirm comments
SELECT * FROM USER_TAB_COMMENTS WHERE TABLE_NAME IN ('DEPT','EMP');

-- 8. Drop First_name column from EMP table and confirm
ALTER TABLE EMP DROP COLUMN First_name;

-- Confirm structure
DESC EMP;
