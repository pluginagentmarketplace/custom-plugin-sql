---
name: sql-fundamentals
description: Master SQL fundamentals including SELECT, INSERT, UPDATE, DELETE, CREATE, ALTER, DROP operations. Learn data types, WHERE clauses, ORDER BY, GROUP BY, and basic joins.
---

# SQL Fundamentals

## Quick Start

### Your First SELECT Query

```sql
-- Select all employees
SELECT * FROM employees;

-- Select specific columns with WHERE clause
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 50000;

-- Order results by salary
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 50000
ORDER BY salary DESC;
```

## Core Concepts

### Data Types

```sql
-- Numeric types
BIGINT, INT, SMALLINT, TINYINT  -- Integer types
DECIMAL(10,2), FLOAT, DOUBLE     -- Decimal types

-- String types
VARCHAR(255), CHAR(10), TEXT     -- Text types

-- Date/Time types
DATE, TIME, TIMESTAMP, DATETIME  -- Temporal types

-- Other types
BOOLEAN, BLOB, JSON, UUID
```

### DDL Operations (Data Definition Language)

```sql
-- Create a table
CREATE TABLE employees (
  id INT PRIMARY KEY AUTO_INCREMENT,
  first_name VARCHAR(100) NOT NULL,
  last_name VARCHAR(100) NOT NULL,
  email VARCHAR(255) UNIQUE,
  salary DECIMAL(10,2),
  hire_date DATE,
  department_id INT,
  FOREIGN KEY (department_id) REFERENCES departments(id)
);

-- Modify a table
ALTER TABLE employees ADD COLUMN phone VARCHAR(20);
ALTER TABLE employees MODIFY COLUMN salary DECIMAL(12,2);
ALTER TABLE employees DROP COLUMN phone;

-- Drop a table
DROP TABLE employees;
```

### DML Operations (Data Manipulation Language)

```sql
-- Insert single row
INSERT INTO employees (first_name, last_name, salary)
VALUES ('John', 'Doe', 75000);

-- Insert multiple rows
INSERT INTO employees (first_name, last_name, salary) VALUES
('Jane', 'Smith', 80000),
('Bob', 'Johnson', 70000);

-- Update records
UPDATE employees
SET salary = 85000
WHERE first_name = 'John';

-- Delete records
DELETE FROM employees WHERE id = 1;
```

### Query Filtering

```sql
-- WHERE with various operators
SELECT * FROM employees WHERE salary > 50000;
SELECT * FROM employees WHERE salary BETWEEN 40000 AND 80000;
SELECT * FROM employees WHERE first_name IN ('John', 'Jane', 'Bob');
SELECT * FROM employees WHERE email IS NOT NULL;
SELECT * FROM employees WHERE first_name LIKE 'J%';  -- Starts with J
```

### Sorting Results

```sql
-- Single column sorting
SELECT * FROM employees ORDER BY salary DESC;

-- Multiple column sorting
SELECT * FROM employees
ORDER BY department_id ASC, salary DESC;

-- LIMIT results
SELECT * FROM employees
ORDER BY salary DESC
LIMIT 10;  -- Top 10 highest paid
```

## Aggregate Functions

```sql
-- Count, Sum, Average
SELECT COUNT(*) as employee_count FROM employees;
SELECT SUM(salary) as total_salary FROM employees;
SELECT AVG(salary) as avg_salary FROM employees;
SELECT MIN(salary) as min_salary, MAX(salary) as max_salary FROM employees;

-- Group By
SELECT department_id, COUNT(*) as emp_count, AVG(salary) as avg_salary
FROM employees
GROUP BY department_id;

-- Having clause (filter groups)
SELECT department_id, COUNT(*) as emp_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

## Basic JOINs

```sql
-- INNER JOIN
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id;

-- LEFT JOIN
SELECT e.first_name, e.last_name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id;

-- Multiple joins
SELECT e.first_name, d.department_name, p.project_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id
INNER JOIN projects p ON e.id = p.employee_id;
```

## Common String Functions

```sql
-- Concatenation
SELECT CONCAT(first_name, ' ', last_name) as full_name FROM employees;

-- Length
SELECT first_name, LENGTH(first_name) as name_length FROM employees;

-- Substring
SELECT SUBSTRING(email, 1, POSITION('@' IN email)-1) as username FROM employees;

-- Case functions
SELECT UPPER(first_name), LOWER(last_name) FROM employees;
SELECT TRIM(first_name) FROM employees;
```

## Date Functions

```sql
-- Current date/time
SELECT CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP;

-- Extract parts
SELECT YEAR(hire_date), MONTH(hire_date), DAY(hire_date)
FROM employees;

-- Date arithmetic
SELECT first_name, hire_date,
       DATEDIFF(CURRENT_DATE, hire_date) as days_employed
FROM employees;

SELECT first_name, hire_date,
       DATE_ADD(hire_date, INTERVAL 1 YEAR) as one_year_anniversary
FROM employees;
```

## Next Steps

Learn Advanced SQL including complex joins, subqueries, CTEs, and window functions in the `advanced-sql` skill.
