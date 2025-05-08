
## SQL vs MySQL

### SQL
- SQL (Structured Query Language) is a standard language used for managing and manipulating relational databases.
- It is used to query, insert, update, and delete data in databases.
- SQL is not a database itself but a language that works with relational database management systems (RDBMS).

### MySQL
- MySQL is an open-source RDBMS that uses SQL as its query language.
- It is a database management system where data is stored, managed, and retrieved using SQL commands.
- MySQL supports SQL for querying and managing data, but it also has its own specific features and optimizations.

### Key Difference
- **SQL** is the language used to interact with databases, while **MySQL** is a database system that uses SQL.

### DELETE

- `DELETE` command is used to delete a row from the table.
- This is a **DML** (Data Manipulation Language) command.
- It is **slower** than `TRUNCATE`.
- You **can rollback** data after executing the `DELETE` statement.

### TRUNCATE

- `TRUNCATE` deletes **all rows** from the table.
- This is a **DDL** (Data Definition Language) command.
- It is **faster** than `DELETE`.
- You **can't rollback** data after using `TRUNCATE`.

---

### What are the different subsets of SQL?

#### ✅ DDL (Data Definition Language):
- `CREATE`, `ALTER`, `RENAME`, `TRUNCATE`, `DROP`

#### ✅ DQL (Data Query Language):
- `SELECT`

#### ✅ DML (Data Manipulation Language):
- `INSERT`, `UPDATE`, `DELETE`

#### ✅ DCL (Data Control Language):
- `GRANT`, `REVOKE`

#### ✅ TCL (Transaction Control Language):
- `START TRANSACTION`, `COMMIT`, `ROLLBACK`

### What do you mean by DBMS? What are its different types?

**DBMS (Database Management System)** is software that helps in storing, managing, and retrieving data from a database easily and efficiently. It acts as an interface between the database and the users or application programs.

#### Types of DBMS:

1. **Hierarchical DBMS**  
   - Data is organized in a tree-like structure (parent-child).

2. **Network DBMS**  
   - Data is organized as a graph, allowing many-to-many relationships.

3. **Relational DBMS (RDBMS)**  
   - Data is stored in tables (rows and columns).  
   - Example: MySQL, PostgreSQL, Oracle.

4. **Object-Oriented DBMS (OODBMS)**  
   - Data is stored in the form of objects (like in object-oriented programming).


### What do you mean by table and field in SQL?

- **Table**: A collection of related data organized in rows and columns. It represents a real-world entity like `Students` or `Products`.

- **Field**: A column in a table that stores a specific piece of data. For example, in a `Students` table, `Name`, `Age`, and `Class` are fields.


### `CHAR`
- Used for storing fixed-length strings. If the string is shorter than the defined length, the remaining space is padded with spaces.
- Example: `CHAR(10)` will store a string of exactly 10 characters, padding with spaces if necessary.

### `VARCHAR`
- Used for storing variable-length strings. It only takes up as much space as the string requires, without padding.
- Example: `VARCHAR(50)` can store a string of up to 50 characters, but if the string is shorter, it will take up only the space needed.

<!-- =========================KEYS========================= -->
### UNIQUE Key
- A `UNIQUE` key constraint ensures that all values in a column are distinct (i.e., no two rows can have the same value in the specified column). Unlike the `PRIMARY KEY`, it allows NULL values, but only one NULL value is allowed in a column with a unique constraint.
- The unique constraint can be applied to one or more columns in a table.
- A table can have multiple `UNIQUE` constraints, but only one `PRIMARY KEY`.

- Example:
```sql
CREATE TABLE employees (
  employee_id INT PRIMARY KEY,
  email VARCHAR(100) UNIQUE
);

### Primary Key
- A primary key is a column or a set of columns in a table that uniquely identifies each row in that table. A primary key must contain unique values, and it cannot contain NULL values.
- Example: 
```sql
CREATE TABLE employees (
  employee_id INT PRIMARY KEY,
  name VARCHAR(100),
  age INT
);```
### FOREIGN KEY
- A `FOREIGN KEY` is a column or a set of columns in one table that is used to establish a link between the data in two tables. It is used to enforce referential integrity between the two tables.
- A `FOREIGN KEY` in one table points to a `PRIMARY KEY` or `UNIQUE` key in another table.
- This relationship ensures that data in the foreign key column matches data in the referenced primary or unique key column.

- Example:
```sql
CREATE TABLE departments (
  department_id INT PRIMARY KEY,
  department_name VARCHAR(100)
);

CREATE TABLE employees (
  employee_id INT PRIMARY KEY,
  name VARCHAR(100),
  department_id INT,
  FOREIGN KEY (department_id) REFERENCES departments(department_id)
);```
### Constraints
- Constraints are rules applied to columns in a table to ensure data integrity and accuracy. They define the conditions for data to be stored in a table.
- Common types of constraints include:
  - **NOT NULL**: Ensures that a column cannot have NULL values.
  - **UNIQUE**: Ensures that all values in a column are unique.
  - **PRIMARY KEY**: Uniquely identifies each record in a table (combines `NOT NULL` and `UNIQUE`).
  - **FOREIGN KEY**: Ensures referential integrity between two tables.
  - **CHECK**: Ensures that values in a column satisfy a specific condition.
  - **DEFAULT**: Provides a default value for a column when no value is specified.
  - **INDEX**: this constraints is used to create and retrieve data from database very quickly.

- Example:
```sql
CREATE TABLE employees (
  employee_id INT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  age INT CHECK (age >= 18),
  department_id INT,
  FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```
## SQL Keywords with Short Definitions and Examples

### 1. `SELECT`
- Used to fetch data from a database.
- Example: `SELECT name FROM students;`

### 2. `FROM`
- Specifies the table to fetch data from.
- Example: `SELECT * FROM employees;`

### 3. `WHERE`
- Filters records based on a condition.
- Example: `SELECT * FROM products WHERE price > 100;`

### 4. `INSERT`
- Adds new data to a table.
- Example: `INSERT INTO users (name, age) VALUES ('John', 25);`

### 5. `UPDATE`
- Modifies existing data in a table.
- Example: `UPDATE users SET age = 30 WHERE name = 'John';`

### 6. `DELETE`
- Removes records from a table.
- Example: `DELETE FROM users WHERE age < 18;`

---

### 7. `CREATE`
- Creates a new table, database, etc.
- Example: `CREATE TABLE books (id INT, title VARCHAR(100));`

### 8. `ALTER`
- Modifies the structure of an existing table.
- Example: `ALTER TABLE books ADD author VARCHAR(50);`

### 9. `DROP`
- Deletes a table or database permanently.
- Example: `DROP TABLE books;`

### 10. `TRUNCATE`
- Deletes all rows from a table quickly.
- Example: `TRUNCATE TABLE logs;`

---

### 11. `JOIN`
- Combines rows from two or more tables.
- Example: `SELECT * FROM orders JOIN customers ON orders.customer_id = customers.id;`

### 12. `GROUP BY`
- Groups rows that have the same values.
- Example: `SELECT category, COUNT(*) FROM products GROUP BY category;`

### 13. `ORDER BY`
- Sorts the result set.
- Example: `SELECT * FROM students ORDER BY marks DESC;`

### 14. `HAVING`
- Filters groups created by `GROUP BY`.
- Example: `SELECT department, COUNT(*) FROM employees GROUP BY department HAVING COUNT(*) > 5;`

### 15. `DISTINCT`
- Removes duplicate values.
- Example: `SELECT DISTINCT city FROM customers;`

---

### 16. `IN`
- Checks if a value exists in a list.
- Example: `SELECT * FROM products WHERE category IN ('Electronics', 'Books');`

### 17. `BETWEEN`
- Filters values within a range.
- Example: `SELECT * FROM orders WHERE amount BETWEEN 100 AND 500;`

### 18. `LIKE`
- Searches for a pattern.
- Example: `SELECT * FROM users WHERE name LIKE 'A%';`

### 19. `IS NULL`
- Checks for NULL values.
- Example: `SELECT * FROM employees WHERE manager_id IS NULL;`

---

### 20. `UNION`
- Combines the result of two `SELECT` statements.
- Example: `SELECT name FROM students UNION SELECT name FROM teachers;`

### 21. `EXISTS`
- Checks if a subquery returns any records.
- Example: `SELECT name FROM customers WHERE EXISTS (SELECT * FROM orders WHERE customers.id = orders.customer_id);`

### 22. `ANY`
- Compares a value with any value in a subquery.
- Example: `SELECT * FROM products WHERE price > ANY (SELECT price FROM products WHERE category = 'Books');`

### 23. `ALL`
- Compares a value with all values in a subquery.
- Example: `SELECT * FROM products WHERE price < ALL (SELECT price FROM products WHERE category = 'Electronics');`


### 24. `CASE`
- Provides if-else logic in SQL.
- Example:
```sql
SELECT name,
  CASE
    WHEN marks >= 90 THEN 'A'
    WHEN marks >= 75 THEN 'B'
    ELSE 'C'
  END AS grade
FROM students;
```

---

### 25. `GRANT`
- Gives permissions to users.
- Example:
```sql
GRANT SELECT ON employees TO user1;
```

---

### 26. `REVOKE`
- Removes permissions from users.
- Example:
```sql
REVOKE SELECT ON employees FROM user1;
```

---

### 27. `COMMIT`
- Saves all changes made during a transaction.
- Example:
```sql
COMMIT;
```

---

### 28. `ROLLBACK`
- Undoes changes made during the current transaction.
- Example:
```sql
ROLLBACK;
```

---

### 29. `SAVEPOINT`
- Sets a point to which you can rollback later.
- Example:
```sql
SAVEPOINT sp1;
-- Perform some SQL operations
ROLLBACK TO sp1;
```

### Data Integrity
- **Data Integrity** refers to the accuracy, consistency, and reliability of data stored in a database. It ensures that data is stored correctly and remains accurate and consistent over its lifecycle.
- Data integrity is crucial for maintaining high-quality, error-free data in relational databases and is enforced through constraints like `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`, and `NOT NULL`.

Types of Data Integrity:
1. **Entity Integrity**: Ensures that each record in a table is unique and identifiable using a `PRIMARY KEY`.
2. **Referential Integrity**: Ensures that relationships between tables are consistent, typically enforced with `FOREIGN KEY` constraints.
3. **Domain Integrity**: Ensures that data entered into a database is valid and within a specific domain (e.g., a valid range of numbers or correct data types).
4. **User-Defined Integrity**: Involves rules defined by the user or application to maintain data consistency.

- Example:
```sql
CREATE TABLE students (
  student_id INT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) UNIQUE
);
```

### Clustered Index
- A **Clustered Index** determines the physical order of data rows in a table. When you create a clustered index on a table, the rows are stored in the same order as the index.
- A table can have only one clustered index because the data rows can only be sorted in one order.
- By default, the `PRIMARY KEY` constraint creates a clustered index.
- Clustered indexes are faster for retrieving data when the rows are returned in order.

- Example:
```sql
CREATE TABLE employees (
  employee_id INT PRIMARY KEY, -- Automatically creates a clustered index
  name VARCHAR(100)
);
```

### Non-Clustered Index
- A **Non-Clustered Index** is an index where the data is stored separately from the table. It does not change the physical order of the rows in the table but instead creates a separate structure that holds the indexed columns and pointers to the actual rows.
- Non-clustered indexes are helpful for improving the speed of queries that search on non-primary key columns.
- A table can have multiple non-clustered indexes.
  
- Features:
  - Does not affect the physical order of data in the table.
  - Can have multiple non-clustered indexes on a table.
  - Stores a pointer to the actual data rows, which improves performance when querying based on indexed columns.
  
- Example:
```sql
CREATE INDEX idx_employee_name ON employees (name);
```

## Types of JOINS in SQL

### 1. INNER JOIN
- Returns records that have matching values in both tables.
- If there is no match, the row is not included in the result set.
  
- Example:
```sql
SELECT employees.name, departments.name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```

### 2. LEFT JOIN (or LEFT OUTER JOIN)
- Returns all records from the left table (table1), and the matched records from the right table (table2). If there is no match, NULL values are returned for columns from the right table.
  
- Example:
```sql
SELECT employees.name, departments.name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.department_id;
```

### 3. RIGHT JOIN (or RIGHT OUTER JOIN)
- Returns all records from the right table (table2), and the matched records from the left table (table1). If there is no match, NULL values are returned for columns from the left table.
  
- Example:
```sql
SELECT employees.name, departments.name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.department_id;
```

### 4. FULL JOIN (or FULL OUTER JOIN)
- Returns records when there is a match in either the left table (table1) or the right table (table2). If there is no match, NULL values are returned for columns from the table without a match.
  
- Example:
```sql
SELECT employees.name, departments.name
FROM employees
FULL JOIN departments ON employees.department_id = departments.department_id;
```

### 5. CROSS JOIN
- Returns the Cartesian product of both tables, i.e., it combines every row of the first table with every row of the second table.
  
- Example:
```sql
SELECT employees.name, departments.name
FROM employees
CROSS JOIN departments;
```

### Denormalization
- The process of intentionally introducing redundancy into a database by merging tables, usually for the purpose of improving read performance. Denormalization is the opposite of normalization, which seeks to minimize redundancy.

- Denormalization can make data retrieval faster because fewer joins are needed, but it can also lead to data anomalies and increased storage costs.
  
- Example: Instead of having separate tables for `orders` and `order_details`, you could merge them into one table to speed up read queries that need both datasets at once. However, this would increase redundancy (duplicate data) and require more careful handling of updates and deletions.

```sql
-- Example of denormalization by combining order and order details
CREATE TABLE orders_and_details AS
SELECT o.order_id, o.customer_id, o.order_date, od.product_id, od.quantity
FROM orders o
JOIN order_details od ON o.order_id = od.order_id;
```

### Entities
- In the context of databases, an **entity** represents a real-world object or concept that can be distinctly identified. Entities are typically represented as tables in a relational database, and each entity will have a set of attributes (fields) that describe it.

- An entity can be a person, object, event, or anything else that can be represented in a database. Each record (or row) in the table represents a unique instance of that entity.

- Example: In a database for a library system, the entities might include:
  - **Books** (with attributes like title, author, ISBN)
  - **Members** (with attributes like name, membership_id, contact info)
  - **Loans** (with attributes like book_id, member_id, loan_date)

```sql
-- Example of an entity in a table
CREATE TABLE books (
  book_id INT PRIMARY KEY,
  title VARCHAR(100),
  author VARCHAR(100),
  isbn VARCHAR(20)
);
```

### Relationship
- In the context of databases, a **relationship** refers to the way in which two or more entities (tables) are connected to each other. Relationships help define how data in one table is related to data in another table.

- There are three main types of relationships in a relational database:
  1. **One-to-One (1:1) Relationship**: Each record in the first table is associated with only one record in the second table, and vice versa.
  2. **One-to-Many (1:M) Relationship**: A record in the first table can be associated with multiple records in the second table, but each record in the second table is associated with only one record in the first table.
  3. **Many-to-Many (M:N) Relationship**: Records in both tables can be associated with multiple records in the other table.

- Example:
  - **One-to-Many**: A single `customer` can have many `orders`. Each `order` belongs to one `customer`.
  - **Many-to-Many**: A `student` can be enrolled in many `courses`, and each `course` can have many `students`.

```sql
-- One-to-Many relationship example: Customer and Orders
CREATE TABLE customers (
  customer_id INT PRIMARY KEY,
  name VARCHAR(100)
);

CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  order_date DATE,
  customer_id INT,
  FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

### What is an Index?

- An **Index** in a database is a data structure that improves the speed of data retrieval operations on a table at the cost of additional space and increased maintenance time for insert, update, and delete operations.

- It works similarly to an index in a book. Instead of searching through the entire table (which can be slow, especially in large datasets), the index allows the database to quickly locate the row based on a specific column or set of columns.

- Indexes are typically created on columns that are frequently used in search conditions (e.g., `WHERE`, `JOIN`), sorting (`ORDER BY`), or grouping (`GROUP BY`).

#### Types of Indexes:
1. **Clustered Index**: The table’s data is physically organized based on the clustered index. Only one clustered index can exist per table.
2. **Non-clustered Index**: The data in the table is not sorted based on the index. You can have multiple non-clustered indexes on a table.
3. **Unique Index**: Ensures that the values in the indexed column(s) are unique.
4. **Composite Index**: An index that is created on multiple columns of the table.

#### Example of Creating an Index:
```sql
-- Creating a simple index on the 'name' column in the 'employees' table
CREATE INDEX idx_employee_name ON employees (name);
```

### Types of Relationships in SQL

There are different types of relationships in a database:

1. **One-to-One Relationship**  
   - This is a connection between two tables in which each record in one table corresponds to a maximum of one record in the other.
   - Example: A table of employees where each employee has a unique company email in a separate table.

2. **One-to-Many / Many-to-One Relationship**  
   - This is the most frequent connection, in which a record in one table is linked to several records in another.
   - Example: A table of departments where each department can have many employees, but each employee belongs to only one department.

3. **Many-to-Many Relationship**  
   - This is used when defining a relationship that requires several instances on each side.
   - Example: A table of students and a table of courses, where each student can enroll in multiple courses, and each course can have multiple students. A junction table is often used to link the two.

4. **Self-Referencing Relationship**  
   - When a table has to declare a connection with itself, this is the method to employ.
   - Example: An employee table where an employee has a manager, and the manager is also an employee in the same table. The `employee_id` and `manager_id` columns would reference the same table.

### What is OLTP?

OLTP (Online Transaction Processing) allows many people to perform a large number of database transactions in real-time, typically over the internet. A database transaction involves changing, adding, removing, or querying data in a database.


### Differences Between OLTP and OLAP

- **OLTP** (Online Transaction Processing): Used for online database modifications (e.g., adding, updating, deleting data).
- **OLAP** (Online Analytical Processing): Used for querying and analyzing large sets of data for reports and insights.

### How to Create Empty Tables with the Same Structure as Another Table?

To create an empty table with the same structure as another table, you can use the `CREATE TABLE` statement with a `SELECT` query that does not return any data:

```sql
CREATE TABLE new_table AS
SELECT * FROM existing_table WHERE 1=0;
```

### What is PostgreSQL?

PostgreSQL is an open-source, relational database management system (RDBMS) that is known for its robustness, extensibility, and support for SQL (Structured Query Language). It allows users to store, manipulate, and query data efficiently and supports advanced features like ACID compliance, complex queries, and foreign keys.


### What is the usage of the NVL() function?

The `NVL()` function in SQL is used to replace `NULL` values with a specified value. It is commonly used to handle missing or undefined data by substituting `NULL` with a default value.

**Syntax:**
```sql
NVL(expression, replacement_value)
```

### What is the difference between the RANK() and DENSE_RANK() functions?

The `RANK()` and `DENSE_RANK()` functions are both used to assign a rank to rows within a result set, but they handle ties differently:

1. **RANK()**: 
   - Assigns a unique rank to each row.
   - If two rows have the same value (tie), they get the same rank, but the next rank will be skipped.
   - Example: If two rows are ranked 1, the next rank will be 3 (skipping 2).

   **Example:**
   ```sql
   SELECT employee_name, salary, RANK() OVER (ORDER BY salary DESC) AS rank
   FROM employees;
```
2. **DENSE_RANK()**;

The `DENSE_RANK()` function is used to assign a rank to each row within a result set, where rows with equal values receive the same rank, but the next rank is not skipped.

- **How it works**: When two or more rows have the same value (tie), they will receive the same rank, and the next rank is assigned without skipping any numbers.
  
  For example, if two rows are ranked 1, the next rank will be 2, not 3 as in the case of `RANK()`.

**Example:**
```sql
SELECT employee_name, salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank
FROM employees;
```
### Q25. What are some common clauses used with SELECT query in SQL?

Here are some commonly used clauses with the `SELECT` query:

- **FROM**: Specifies the table to select or delete data from.  
  Example: `SELECT * FROM employees;`

- **WHERE**: Filters rows based on a condition.  
  Example: `SELECT * FROM employees WHERE salary > 50000;`

- **GROUP BY**: Groups rows sharing a property (used with aggregate functions).  
  Example: `SELECT department, COUNT(*) FROM employees GROUP BY department;`

- **HAVING**: Filters groups based on a condition (used with `GROUP BY`).  
  Example: `SELECT department, COUNT(*) FROM employees GROUP BY department HAVING COUNT(*) > 5;`

- **ORDER BY**: Sorts the result set.  
  Example: `SELECT * FROM employees ORDER BY salary DESC;`

- **JOIN**: Combines rows from two or more tables based on a related column.  
  Example: `SELECT * FROM orders JOIN customers ON orders.customer_id = customers.id;`

- **LIMIT** (or `TOP` in some databases): Limits the number of rows returned.  
  Example: `SELECT * FROM employees LIMIT 10;`

These clauses help refine and organize the results returned by a `SELECT` query.


