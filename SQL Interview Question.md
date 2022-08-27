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
