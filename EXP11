1 DECLARE
    v_emp_id     NUMBER := 110;
    v_salary     EMPLOYEES.SALARY%TYPE;
    v_incentive  NUMBER;
BEGIN
    SELECT SALARY INTO v_salary
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID = v_emp_id;

    v_incentive := v_salary * 0.10;

    DBMS_OUTPUT.PUT_LINE('Employee ID: ' || v_emp_id);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);
    DBMS_OUTPUT.PUT_LINE('Incentive (10%): ' || v_incentive);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Employee with ID ' || v_emp_id || ' not found.');
END;
/
2 DECLARE
    "MyVar" NUMBER := 10;  -- quoted identifier (case-sensitive)
    myvar   NUMBER := 20;  -- unquoted identifier (case-insensitive)
BEGIN
    DBMS_OUTPUT.PUT_LINE("MyVar");  -- valid
    DBMS_OUTPUT.PUT_LINE(MyVar);    -- invalid case-insensitive reference to quoted identifier
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: Invalid case-insensitive reference to quoted identifier.');
END;
/
3 DECLARE
    v_emp_id NUMBER := 122;
    v_salary EMPLOYEES.SALARY%TYPE;
BEGIN
    SELECT SALARY INTO v_salary
    FROM EMPLOYEES
    WHERE EMPLOYEE_ID = v_emp_id;

    v_salary := v_salary * 1.15;  -- increase by 15%

    UPDATE EMPLOYEES
    SET SALARY = v_salary
    WHERE EMPLOYEE_ID = v_emp_id;

    DBMS_OUTPUT.PUT_LINE('Salary updated successfully for employee ' || v_emp_id);
    DBMS_OUTPUT.PUT_LINE('New Salary: ' || v_salary);

    COMMIT;
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Employee with ID ' || v_emp_id || ' not found.');
END;
/
4 CREATE OR REPLACE PROCEDURE check_nulls IS
    v_value1 NUMBER := NULL;
    v_value2 NUMBER := 10;
BEGIN
    IF v_value1 IS NULL AND v_value2 IS NOT NULL THEN
        DBMS_OUTPUT.PUT_LINE('Condition is TRUE because v_value1 IS NULL and v_value2 IS NOT NULL.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('Condition is FALSE.');
    END IF;
END;
/

-- Execute the procedure
BEGIN
    check_nulls;
END;
/
5 DECLARE
    v_name EMPLOYEES.LAST_NAME%TYPE;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Employees whose last name starts with "S":');
    FOR rec IN (
        SELECT LAST_NAME FROM EMPLOYEES
        WHERE LAST_NAME LIKE 'S%'
    ) LOOP
        DBMS_OUTPUT.PUT_LINE(rec.LAST_NAME);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE(CHR(10) || 'Employees whose last name contains "_" character:');
    FOR rec IN (
        SELECT LAST_NAME FROM EMPLOYEES
        WHERE LAST_NAME LIKE '%\_%' ESCAPE '\'
    ) LOOP
        DBMS_OUTPUT.PUT_LINE(rec.LAST_NAME);
    END LOOP;
END;
/
