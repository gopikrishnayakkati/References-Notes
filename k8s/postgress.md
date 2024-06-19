## Create a Database
```sql
-- Create a new database named "mydatabase"
CREATE DATABASE mydatabase;

-- Connect to the new database
\c mydatabase
```
## Create Tables
```sql
-- Create a table named "employees"
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100),
    department VARCHAR(50)
);

-- Create a table named "orders"
CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    employee_id INTEGER,
    order_date DATE,
    total DECIMAL(10, 2),
    FOREIGN KEY (employee_id) REFERENCES employees(id)
);
```

## Insert Values
```sql
-- Insert values into the "employees" table
INSERT INTO employees (name, email, department)
VALUES
    ('John Doe', 'johndoe@example.com', 'Sales'),
    ('Jane Smith', 'janesmith@example.com', 'Marketing'),
    ('Bob Johnson', 'bobjohnson@example.com', 'IT');

-- Insert values into the "orders" table
INSERT INTO orders (employee_id, order_date, total)
VALUES
    (1, '2022-01-01', 100.00),
    (1, '2022-01-15', 200.00),
    (2, '2022-02-01', 50.00),
    (3, '2022-03-01', 300.00);
```
## Query Commands
```sql
-- Retrieve all rows from the "employees" table
SELECT * FROM employees;

-- Retrieve all rows from the "orders" table
SELECT * FROM orders;

-- Retrieve all rows from the "orders" table where the total is greater than 100
SELECT * FROM orders WHERE total > 100;

-- Retrieve the total order value for each employee
SELECT e.name, SUM(o.total) AS total_orders
FROM employees e
JOIN orders o ON e.id = o.employee_id
GROUP BY e.name;

-- Retrieve the employee with the highest total order value
SELECT e.name, SUM(o.total) AS total_orders
FROM employees e
JOIN orders o ON e.id = o.employee_id
GROUP BY e.name
ORDER BY total_orders DESC
LIMIT 1;
```
Additional Commands
```sql
-- Drop the "orders" table
DROP TABLE orders;

-- Drop the "employees" table
DROP TABLE employees;

-- Drop the "mydatabase" database
DROP DATABASE mydatabase;
```

These commands demonstrate basic database operations in PostgreSQL, including creating a database, creating tables, inserting values, and querying data.
in postgress
Sources



postgresql.org favicon
postgresql.org favicon
View 2 more
Answer
To securely pass environment variables for PostgreSQL host names, you can use the PGHOST environment variable. This variable specifies the hostname or IP address of the PostgreSQL server. Here is how you can use it:
```bash
PGHOST=$HOST psql -U myuser mydb
```