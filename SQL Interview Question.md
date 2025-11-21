#  SQL 

## 1. SQL Sub-Languages
SQL has **four main sub-languages**:

### **1.1 DDL – Data Definition Language**
Used to define or modify database structures.  
**Examples:** `CREATE`, `DROP`, `ALTER`, `TRUNCATE`

### **1.2 DQL – Data Query Language**
Used for querying data.  
**Examples:** `SELECT`

### **1.3 DML – Data Manipulation Language**
Used to modify table records.  
**Examples:** `INSERT`, `UPDATE`, `DELETE`

### **1.4 DCL – Data Control Language**
Used to manage permissions.  
**Examples:** `GRANT`, `REVOKE`

---

# 2. DDL – CREATE, ALTER, DROP

## **2.1 CREATE TABLE**
```sql
CREATE TABLE student (
    student_id VARCHAR(20) PRIMARY KEY,
    student_name VARCHAR(50) NOT NULL,
    student_age INT
);
```

Another example:
```sql
CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(20),
    age INT
);
```

### Copy Table Structure + Data
```sql
CREATE TABLE emp2 AS SELECT * FROM emp1;
```

### Copy Only Structure (No Data)
```sql
CREATE TABLE emp2 AS SELECT * FROM emp1 WHERE 1 = 2;
```

---

## **2.2 ALTER TABLE**

### Add Column
```sql
ALTER TABLE emp ADD (address VARCHAR(100));
```

### Add Multiple Columns
```sql
ALTER TABLE emp
ADD (dob DATE, father_name VARCHAR(20), mother_name VARCHAR(20));
```

### Modify Column
```sql
ALTER TABLE emp MODIFY (address VARCHAR(200));
```

### Rename Column
```sql
ALTER TABLE emp RENAME COLUMN address TO location;
```

---

## **2.3 DROP**
Deletes **objects**.

### Drop Column
```sql
ALTER TABLE emp DROP COLUMN dob;
```

### Drop Multiple Columns
```sql
ALTER TABLE emp DROP (father_name, mother_name);
```

### Drop Constraint
```sql
ALTER TABLE emp DROP CONSTRAINT primary_id;
```

---

# 3. SELECT (DQL)

### Basic Queries
```sql
SELECT * FROM student;
SELECT student_name, student_age FROM student;
SELECT DISTINCT(student_name) FROM student;
```

### With WHERE
```sql
SELECT * FROM student WHERE student_age > 18;
```

### Column Alias
```sql
SELECT name, salary * 12 AS annual_salary FROM emp;
```

### TOP (SQL Server)
```sql
SELECT TOP 3 * FROM emp ORDER BY salary DESC;
```

---

# 4. ORDER BY
```sql
SELECT * FROM student ORDER BY score ASC;
SELECT * FROM student ORDER BY score DESC;
SELECT * FROM student ORDER BY score DESC, country ASC;
```

---

# 5. GROUP BY & HAVING

### GROUP BY
```sql
SELECT country, SUM(score) AS total_score
FROM student
GROUP BY country;
```

### HAVING (after aggregation)
```sql
SELECT country, SUM(score) AS total_score
FROM student
GROUP BY country
HAVING SUM(score) > 800;
```

---

# 6. INSERT

### Insert All Columns
```sql
INSERT INTO student VALUES ('1a', 'Aman Singh', 20);
```

### Insert Selected Columns
```sql
INSERT INTO student (student_id, student_name)
VALUES ('3a', 'Tripti Singh');
```

### Insert From Another Table
```sql
INSERT INTO table2
SELECT * FROM table1;
```

---

# 7. UPDATE

```sql
UPDATE emp
SET sal = 5000, com = 300
WHERE job = 'ANALYST';
```

### Update using Subquery
```sql
UPDATE emp
SET job = (SELECT dname FROM dept WHERE ROWNUM = 1);
```

---

# 8. DELETE vs TRUNCATE

| Feature | DELETE | TRUNCATE |
|--------|--------|-----------|
| Removes | Rows | All Rows |
| WHERE allowed | ✔ Yes | ❌ No |
| Rollback allowed | ✔ Yes | ❌ No |
| Speed | Slower | Faster |
| Resets identity | ❌ No | ✔ Yes |

---

# 9. BETWEEN
```sql
SELECT * FROM emp WHERE sal BETWEEN 2000 AND 3000;
SELECT * FROM emp WHERE hiredate BETWEEN '1981-04-02' AND '1981-06-09';
```

---

# 10. LIKE (Pattern Matching)

| Pattern | Meaning |
|---------|---------|
| `'a%'` | Starts with a |
| `'%a'` | Ends with a |
| `'%ab%'` | Contains ab |
| `'_ab'` | ab starting at position 2 |
| `'a__'` | a followed by 2 letters |

Examples:
```sql
SELECT * FROM emp WHERE name LIKE 'A%M';
SELECT * FROM emp WHERE name NOT LIKE 'A%';
```

---

# 11. AND / OR / NOT (Logical Operators)

### Using AND
```sql
SELECT * FROM student
WHERE country = 'India' AND score > 500;
```

### Using OR
```sql
SELECT * FROM student
WHERE country = 'India' OR country = 'USA';
```

---

# 12. JOINS

### INNER JOIN
(Returns matching rows)
```sql
SELECT *
FROM A INNER JOIN B
ON A.id = B.id;
```

### LEFT JOIN
(Return all from left + matching from right)
```sql
SELECT *
FROM A LEFT JOIN B
ON A.id = B.id;
```

### RIGHT JOIN
(Return all from right + matching from left)
```sql
SELECT *
FROM A RIGHT JOIN B
ON A.id = B.id;
```

### FULL OUTER JOIN
```sql
SELECT *
FROM A FULL JOIN B
ON A.id = B.id;
```

### Anti Joins
Left Anti Join:
```sql
SELECT *
FROM A
LEFT JOIN B ON A.id = B.id
WHERE B.id IS NULL;
```

---

# 13. SET OPERATIONS

| Operator | Description |
|----------|-------------|
| UNION | Distinct rows from both queries |
| UNION ALL | All rows including duplicates |
| EXCEPT / MINUS | Rows in first query not in second |
| INTERSECT | Common records |

Example:
```sql
SELECT f_name FROM student
UNION
SELECT f_name FROM teacher;
```

---

# 14. SQL FUNCTIONS

## String Functions
- `UPPER()`, `LOWER()`, `CONCAT()`, `TRIM()`
- `LEFT()`, `RIGHT()`, `SUBSTRING()`
- `LENGTH()`

## Numeric Functions
- `ABS()`, `ROUND()`

## Date Functions
- `GETDATE()`, `DAY()`, `MONTH()`, `YEAR()`
- `DATEADD()`, `DATEDIFF()`, `EOMONTH()`
- `FORMAT()`, `CONVERT()`, `CAST()`

## Aggregate Functions
- `SUM()`, `COUNT()`, `MAX()`, `MIN()`, `AVG()`

## Window Functions
- `ROW_NUMBER()`, `RANK()`, `LAG()`, `LEAD()`

---

# 15. Query Execution Order (Very Important)

| Order | Clause |
|-------|--------|
| 1 | FROM |
| 2 | WHERE |
| 3 | GROUP BY |
| 4 | HAVING |
| 5 | SELECT |
| 6 | ORDER BY |
| 7 | LIMIT / TOP |

Example:
```sql
SELECT TOP 3 *
FROM student
WHERE score > 300
GROUP BY country, score
HAVING COUNT(*) > 1
ORDER BY score DESC;
```

---

# 🔥 SQL Interview Questions + Answers

### **Q1. What is the difference between WHERE and HAVING?**
**WHERE** filters rows **before aggregation**.  
**HAVING** filters rows **after aggregation**.

### **Q2. Difference between UNION and UNION ALL?**
- **UNION** removes duplicates.  
- **UNION ALL** keeps duplicates (faster).

### **Q3. What is a Primary Key?**
- Uniquely identifies each row.  
- Cannot contain NULL.  
- One per table.

### **Q4. Primary Key vs Unique Key**
| Feature | Primary Key | Unique Key |
|---------|--------------|-------------|
| Null allowed | ❌ No | ✔ Yes (only one) |
| Count | 1 per table | Many per table |

### **Q5. What is Normalization?**
A process to reduce redundancy and improve data integrity.

### **Q6. What is a Window Function?**
Calculations across rows **without reducing** results.

```sql
SELECT emp_id, salary,
RANK() OVER (ORDER BY salary DESC) AS rank
FROM emp;
```

### **Q7. DELETE vs TRUNCATE vs DROP**
| Command | What it Removes | Rollback? |
|---------|------------------|-----------|
| DELETE | Rows | ✔ Yes |
| TRUNCATE | All rows | ❌ No |
| DROP | Table | ❌ No |

### **Q8. What is ACID?**
- Atomicity
- Consistency
- Isolation
- Durability

### **Q9. What is a Foreign Key?**
Ensures **referential integrity** between tables.

### **Q10. CHAR vs VARCHAR**
| CHAR | VARCHAR |
|------|----------|
| Fixed length | Variable length |
| Faster | Slower |
| Uses full allocated space | Uses actual space |

---

## Advanced SQL Concepts

### ACID Properties
**ACID** ensures reliable database transactions:
- **Atomicity** – A transaction is all‑or‑nothing. If one part fails, the entire transaction rolls back.
- **Consistency** – Ensures the database moves from one valid state to another.
- **Isolation** – Transactions execute independently without interfering.
- **Durability** – Once committed, data is permanently saved even during failures.

**ACID Transaction Flow Diagram:**
```
[START] → [BEGIN TRANSACTION]
       → [EXECUTE OPERATIONS]
       → (Success?) — Yes → [COMMIT] → [END]
                      └ No → [ROLLBACK] → [END]
```

---

### Normalization
Normalization reduces redundancy and improves data integrity.

#### **1NF (First Normal Form)**
- No repeating groups
- Each cell holds a single value

#### **2NF (Second Normal Form)**
- Must be in 1NF
- No partial dependency on a composite primary key

#### **3NF (Third Normal Form)**
- Must be in 2NF
- No transitive dependency (non‑key depending on another non‑key)

**Normalization Visual Example:**
```
UNNORMALIZED:
OrderID | Customer | CustomerCity | Product | Qty

NORMALIZED:
CUSTOMER: CustomerID | Name | City
ORDER: OrderID | CustomerID | Date
ORDER_ITEMS: OrderID | ProductID | Qty
```

---

### Indexing
Indexes speed up read queries by creating a fast lookup structure.

#### Types of Indexes
- **B‑Tree Index** – Default for most DBs, ideal for ranges
- **Hash Index** – Fast equality lookups
- **Composite Index** – Multiple columns
- **Unique Index** – Ensures no duplicates
- **Full‑Text Index** – For searching large text fields

**Index Lookup Diagram:**
```
          [Root]
           /  \
      [Node] [Node]
        /        \
 [Leaf Pages]   [Leaf Pages]
```

**When NOT to use indexes:**
- On very small tables
- Columns with high write operations
- Columns with high repetition (Boolean fields)

---

### Views
A **View** is a virtual table based on a SQL query.

#### Advantages
- Simplifies complex queries
- Provides security (hide sensitive columns)
- Helps create reusable components

#### Types
- **Simple View** – One table
- **Complex View** – Multiple tables and joins
- **Materialized View** – Stores actual data for fast reads

---

### Sharding
Sharding splits large databases horizontally across multiple servers.

**Types of Sharding:**
- **Range Sharding** (based on value ranges)
- **Hash Sharding** (hash function distributes data)
- **Geo Sharding** (region‑based)
- **Directory Sharding** (lookup table decides shard)

**Sharding Architecture Diagram:**
```
                   ┌────────────┐
                   │  App/API   │
                   └─────┬──────┘
                         │
                  ┌──────┴────────┐
                  │  Shard Router │
                  └──────┬────────┘
         ┌───────────────┼────────────────┬───────────────┐
         │               │                │               │
 ┌────────────┐   ┌────────────┐   ┌────────────┐   ┌────────────┐
 │ Shard 1    │   │ Shard 2    │   │ Shard 3    │   │ Shard 4    │
 └────────────┘   └────────────┘   └────────────┘   └────────────┘
```

**When to Use Sharding:**
- Extremely large datasets (TB‑PB scale)
- High throughput applications
- Geo‑distributed systems

---

