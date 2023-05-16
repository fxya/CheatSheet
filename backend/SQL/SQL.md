# SQL Cheat Sheet

### Basic Syntax

```sql
-- Create a table
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);

-- Insert data into a table
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);

-- Select all rows from a table
SELECT * FROM table_name;

-- Select specific columns from a table
SELECT column1, column2, ... FROM table_name;

-- Update rows in a table
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

-- Delete rows from a table
DELETE FROM table_name
WHERE condition;
```

### Data Manipulation

```sql
-- Filter rows using WHERE clause
SELECT column1, column2, ...
FROM table_name
WHERE condition;

-- Sort rows in ascending order
SELECT column1, column2, ...
FROM table_name
ORDER BY column_name ASC;

-- Sort rows in descending order
SELECT column1, column2, ...
FROM table_name
ORDER BY column_name DESC;

-- Limit the number of rows returned
SELECT column1, column2, ...
FROM table_name
LIMIT num_rows;

-- Join two or more tables
SELECT column1, column2, ...
FROM table1
JOIN table2 ON table1.column_name = table2.column_name;

-- Group rows using GROUP BY clause
SELECT column1, COUNT(column2)
FROM table_name
GROUP BY column1;

-- Calculate aggregate functions
SELECT COUNT(column_name)
FROM table_name;

-- Calculate average value
SELECT AVG(column_name)
FROM table_name;

-- Calculate maximum value
SELECT MAX(column_name)
FROM table_name;

-- Calculate minimum value
SELECT MIN(column_name)
FROM table_name;

-- Calculate sum of values
SELECT SUM(column_name)
FROM table_name;
```

### Data Definition

```sql
-- Alter table structure
ALTER TABLE table_name
ADD column_name datatype;

-- Modify column datatype
ALTER TABLE table_name
ALTER COLUMN column_name datatype;

-- Rename table
ALTER TABLE table_name
RENAME TO new_table_name;

-- Delete table
DROP TABLE table_name;
```

### Data Constraints

```sql
-- Add a primary key constraint
ALTER TABLE table_name
ADD CONSTRAINT pk_constraint PRIMARY KEY (column_name);

-- Add a foreign key constraint
ALTER TABLE table_name
ADD CONSTRAINT fk_constraint
FOREIGN KEY (column_name)
REFERENCES referenced_table_name (referenced_column_name);

-- Add a unique constraint
ALTER TABLE table_name
ADD CONSTRAINT unique_constraint UNIQUE (column_name);

-- Add a check constraint
ALTER TABLE table_name
ADD CONSTRAINT check_constraint CHECK (condition);
```

### Advanced Queries

```sql
-- Subqueries
SELECT column1, column2, ...
FROM table_name
WHERE column_name IN (SELECT column_name FROM another_table);

-- Common Table Expressions (CTE)
WITH cte_name AS (
    SELECT column1, column2, ...
    FROM table_name
)
SELECT *
FROM cte_name;

-- Union operator
SELECT column1, column2, ...
FROM table1
UNION
SELECT column1, column2, ...
FROM table2;

-- Union all operator
SELECT column1, column2, ...
FROM table1
UNION ALL
SELECT column1, column2, ...
FROM table2;

-- Case statement
SELECT column_name,
    CASE
        WHEN condition1 THEN value1
        WHEN condition2 THEN value2
        ELSE value3
    END
FROM table_name;
```
