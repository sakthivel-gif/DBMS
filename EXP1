-- 1. Create MY_EMPLOYEE table
CREATE TABLE MY_EMPLOYEE (
    ID NUMBER(4) NOT NULL,
    Last_name VARCHAR2(25),
    First_name VARCHAR2(25),
    Userid VARCHAR2(25),
    Salary NUMBER(9,2)
);

-- 2. Insert first and second rows
INSERT INTO MY_EMPLOYEE VALUES (1, 'Patel', 'Ralph', 'rpatel', 895);
INSERT INTO MY_EMPLOYEE VALUES (2, 'Dancs', 'Betty', 'bdancs', 860);

-- 3. Display the table
SELECT * FROM MY_EMPLOYEE;

-- 4. Insert next two rows using concatenation for userid
INSERT INTO MY_EMPLOYEE (ID, Last_name, First_name, Userid, Salary)
VALUES (3, 'Biri', 'Ben', SUBSTR('B',1,1) || SUBSTR('Biri',1,7), 1100);

INSERT INTO MY_EMPLOYEE (ID, Last_name, First_name, Userid, Salary)
VALUES (4, 'Newman', 'Chad', SUBSTR('C',1,1) || SUBSTR('Newman',1,7), 750);

-- 5. Delete Betty Dancs
DELETE FROM MY_EMPLOYEE WHERE First_name = 'Betty' AND Last_name = 'Dancs';

-- 6. Empty the fourth row (set all columns except ID to NULL)
UPDATE MY_EMPLOYEE
SET Last_name = NULL,
    First_name = NULL,
    Userid = NULL,
    Salary = NULL
WHERE ID = 4;

-- 7. Make data additions permanent
COMMIT;

-- 8. Change last name of employee 3 to Drexler
UPDATE MY_EMPLOYEE
SET Last_name = 'Drexler'
WHERE ID = 3;

-- 9. Change salary to 1000 for employees earning less than 900
UPDATE MY_EMPLOYEE
SET Salary = 1000
WHERE Salary < 900;
