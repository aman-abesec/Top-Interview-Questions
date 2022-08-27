### <b>SQL : </b> There are four type of sub-language

##### 1-DDL(Data Defination language)
    Example: Create, Drop, Alter
##### 2-DQL(Data query language)
    Example: Select
##### 3-DDML(Data Maniplution language)
    Example: Update, Insert, Delete
##### 4-DCL(Data Control language)
    Example: Grant, Revoke

#### CREATE
``` SQL
CREATE TABLE student(
    student_id VARCHAR(20) PRIMARY KEY,
    student_name VARCHAR(20) NOT NULL,
    student_age INT
    );
```

``` SQL
CREATE TABLE student(
    Roll_No INT PRIMARY KEY,
    F_name VARCHAR(20) NOT NULL,
    L_name VARCHAR(20) NOT NULL,
    Age INT
    );
```

#### ALTER & DROP
``` SQL
ALTER TABLE ADD aaddress VARCHAR(500);
ALTER TABLE DROP aaddress;
```

#### SELECT
``` SQL
SELECT * FROM student;
SELECT f_name,l_name FROM student;
SELECT DISTINCT(f_name) FROM student;
SELECT * FROM student WHERE student_id>2;
```
``` SQL
SELECT * FROM student;
SELECT F_name,l_name FROM student;
SELECT * FROM student WHERE dept_no=20;
```
```SQL
SELECT ename,sal*12 AS Annual_sal FROM emp;
SELECT ename,empno,dname,loc FROM emp,dept;
```

#### INSERT
``` SQL
INSERT INTO student VALUES("1a","Aman Singh",20);
INSERT INTO student VALUES("2a","Akash Singh",19);
INSERT INTO student(student_id,student_name) VALUES("3a","Tripti Singh");SQL : There are four type of sub-language
```

#### INSERT All
    Used to add multiple rows with single insert statement.

    INSERT ALL
    INTO mytable(col1,col2,.............coln) VALUES(expr1,expr2,..................exprn)
    INTO mytable(col1,col2,.............coln) VALUES(expr1,expr2,..................exprn)
    INTO mytable(col1,col2,.............coln) VALUES(expr1,expr2,..................exprn)
    SELECT * FROM dual;
    
```SQL
INSERT ALL
INTO mytable1(col1,col2,.............coln) VALUES(expr1,expr2,..................exprn)
INTO mytable1(col1,col2,.............coln) VALUES(expr1,expr2,..................exprn)
INTO mytable2(col1,col2,.............coln) VALUES(expr1,expr2,..................exprn)
SELECT * FROM dual;
```

#### CREATE
``` SQL
CREATE TABLE student(
    student_id VARCHAR(20) PRIMARY KEY,
    student_name VARCHAR(20) NOT NULL,
    student_age INT
    );
```

``` SQL
CREATE TABLE student(
    Roll_No INT PRIMARY KEY,
    F_name VARCHAR(20) NOT NULL,
    L_name VARCHAR(20) NOT NULL,
    Age INT
    );
```

#### ALTER & DROP
``` SQL
ALTER TABLE ADD aaddress VARCHAR(500);
ALTER TABLE DROP aaddress;
```

#### SELECT
``` SQL
SELECT * FROM student;
SELECT f_name,l_name FROM student;
SELECT DISTINCT(f_name) FROM student;
SELECT * FROM student WHERE student_id>2;
```

##### INSERT
``` SQL
INSERT INTO student VALUES("1a","Aman Singh",20);
INSERT INTO student VALUES("2a","Akash Singh",19);
INSERT INTO student(student_id,student_name) VALUES("3a","Tripti Singh");
```
```SQL
# Inserting at run time
INSERT INTO student VALUES(&student_id,&f_name,&l_name);

# Inserting at one By one
enter value for student_id=1
enter value for f_name :Aman
enter value for l_name :Singh

# Inserting one table to another table
INSERT INTO table2 SELECT * FROM table1;
INSERT INTO table2(name) SELECT name FROM table1;
```

#### UPDATE
    UPDATE table_name
      SET col1=val1,col2=val2,...........
      WHERE condition;

```SQL
UPDATE emp
  SET com=300
  WHERE sal<3000;

UPDATE emp
  SET sal=5000,com=300
  WHERE job="ANALYST";

UPDATE emp
  SET sal=5000;
  
# UPDATING one table to another table
UPDATE emp
  set job=(SELECT dname FROM dept
  WHERE rownum=1)
```

#### BETWEEN
    BETWEEN condition allows you to  easily test the condition in (inclusive)
    range within the expression;

    It can be used with SELECT,INSRT,UPDATE or DELETE statement.
```SQL
SELECT * FROM emp
  WHERE sal BETWEEN 2000 AND 3000;

SELECT * FROM emp
  WHERE sal>=2000 AND sal<=3000;

SELECT * FROM emp
WHERE hiredate BETWEEN TO_DATE('1981/04/02','yyyy/mm/dd')
AND TO_DATE('1981/06/09','yyyy/mm/dd')

SELECT * FROM emp
  WHERE sal NOT BETWEEN 2000 AND 3000;

INSERT INTO sample (SELECT * FROM emp WHERE sal BETWEEN 2000 AND 3000);
```

#### DELETE
    DELETE FROM table_name WHERE condition;
```SQL
DELETE FROM emp WHERE ENAME="aMAN";

DELETE FROM emp;//dELETE oNLY data not Table
```
   ### IMPORTANT
    Difference B/W Truncate And Delete
    -DATA CAN NOT BE RESTORED BY TRUNCATE wHILE RESTORE BY DELETE
    -WHERE CONDITION CAN APPLY IN dELETE BUT NOT IN TRUNCATE
