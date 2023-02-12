# Exercise: Create Database, create table and insert dataOpen Lab

# **Goal**

The goal of this exercise is to take you through a step-by-step process for creating a database, creating a table in the database and inserting data into the table. The objective is to provide you with an opportunity to practice how to create a database, a table and insert data.

# **Scenario**

Mr. John Ericson owns a small bookshop. He decides to build a digital database to maintain data about his customers electronically instead of using pen and paper. In this exercise, you’ll build the bookshop database.

# **Instructions**

Please attempt the below tasks before you continue, so you can check and compare your answers with our solution.

Task 1: Create a database called bookshop.

Task 2: Create a table called customers with customer ID, name, and address.

Task 3: Insert a record of data for one customer.

# Solution

1. Create a database called bookshop

```sql
CREATE DATABASE bookshop;
USE bookshop;
```

1. Create a table called “customers” with customer ID, name, and address.

```sql
CREATE TABLE customers (customer_id int, name varchar(100), address varchar(255));
```

1. Insert a record of data for one customer

```sql
INSERT INTO customers (customer_id, name, address)
VALUES (1, "Jack", "115 Old Street");
```

Get content of the customers table after inserting the data:

```sql
SELECT * FROM customers;
```

![Screenshot 2023-01-21 at 2.51.32 PM.png](Exercise%20Create%20Database,%20create%20table%20and%20insert%20%2073f2369805d94854b7720ce7b0f28876/Screenshot_2023-01-21_at_2.51.32_PM.png)