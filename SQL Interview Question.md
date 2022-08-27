### <b>SQL : </b> There are four type of sub-language

##### 1-DDL(Data Defination language)
    Example: Create, Drop, Alter
##### 2-DQL(Data query language)
    Example: Select
##### 3-DML(Data Maniplution language)
    Example: Update, Insert, Delete
##### 4-DCL(Data Control language)
    Example: Grant, Revoke

#### CREATE
    CREATE command is used to create Table;

    CREATE TABLE table_name(
    col1 datatype1(size),
    col2 datatype2(size),
    col3 datatype3(size),
    .
    .
    coln datatypen(size),
    PRIMARY KEY(one or more Column)
    );
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
##### DESC is used to know the structure of the table.
```SQL
DESC table_name;

CREATE TABLE emp as (SELECT * FROM emp1);
CREATE TABLE emp (SELECT name,class,age FROM emp1);
CREATE TABLE emp (SELECT * FROM emp1 where deptno=10);

CREATE TABLE emp as (SELECT ename,job,sal FROM emp1,dept);
```

### IMPORTANT
``` SQL
# NO data will be copy only structure will be copy

CREATE TABLE emp as (SELECT * FROM emp1 where 1=2);
``` 

#### ALTER & DROP
    Alter used with combination of (ADD and DROP);
    Used for changes at column level like constraint changing, renaming one
    column changing data type size;

    ALTER TABLE table_name ADD(column_name datatype);
```SQL
ALTER TABLE emp ADD(Address VARCHAR(15));
ALTER TABLE emp ADD(DOB DATE,FATHERNAME VARCHAR(20),MOTHERNAME VARCHAR(20),Allowness NUMBER(4));

ALTER PRIMARY KEY(empno);

ALTER TABLE emp ADD(Gender CHAR(1) DEFAULT 'F');
```

#### DROP
    DROP is used to delete one or more existing column.
    - DROP constraint
    - DROP a single column
    - DROP multiple column
```SQL
ALTER TABLE DROP(Gender);
ALTER TABLE emp DROP(DOB,FATHERNAME,MOTHERNAME,Allowness);

ALTER TABLE emp DROP constraint Primary_id
``` 

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

#### MODIFY
    MODIFY is used to change the existing column or the size of
    the data type of the existing column.

    ALTER TABLE Table_name MODIFY(column_name datatype);
```SQL
ALTER TABLE emp MODIFY(Address VARCHAR(75));

ALTER TABLE emp MODIFY(Address VARCHAR(75),DOM INT);
``` 
   ### Important
    -You can increase or Decrease the length by any value
    But you can decreaase the value at largest length of value.
```SQL
ALTER TABLE table_name RENAME
  old_column_name TO new_column_name;

ALTER TABLE emp RENAME COLUMN
  Address TO Location1;
```

#### LIKE
    Like operator is used to search specified pattern in the data
    and retrive the record when the pattern is matched;
    'a%' match string starting with 'a';
    '%a' match string ending with 'a';
    'a%z' match string starting with 'a' and ending with 'z';
    '%ab%' match string which contain sub string 'ab';
    '_ab' match string which contain 'ab' at second position from starting.
    'ab_' match string which contain 'ab' at second position from ending.
    'a__'

```SQL
SELECT * FROM emp
  WHERE LIKE 'B%';

'%M%' Ex:-MAN,AMAN;

#  Name of length Five
SELECT name FROM emp
  WHERE name LIKE '_____';

# Name starting with A end with N 
SELECT name FROM emp
  WHERE name LIKE 'A%M';

SELECT name FROM emp
  WHERE name NOT LIKE 'A%M';
 ```

#### AND & OR
     ANd and OR operator is used with WHERE clause for precious filtration
     of data from the database tables by combining more than one condition along
     with select, update and delete queries.

    Defination: The and result true only when all the conjunction of condition
    specified after the where clause are satisfied.
```SQL
SELECT col1, col2,..........
FROM table_name
WHERE condition1 AND condition2 AND condition3.....;
```

    Defination: Among multiple condition specified in the WHERE clause
    the transaction is performed if any of the condition becomes
    true.
```SQL
SELECT col1,col2,...........
FROM table_name
WHERE condition1 OR condition2 OR condition3......;
```
