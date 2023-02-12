# Lab: Exercise: Record deletion

# **Goal**

The goal of this exercise is to teach you how to delete records. You will have the opportunity to practice deleting a record from a table in a database.

# **Scenario**

Mr. John Ericson owns a small bookshop. His bookshop database includes a “Customers” table that contains the bookshop’s customers’ details. The image below displays all records of data stored in the customers’ table.

![Untitled](Lab%20Exercise%20Record%20deletion%20b2ea679b3d254006b9969096ae7ada71/Untitled.png)

Mr. Ericson wants to remove the customer record of Jimmy with ID number 3.

# Solution

1. Create “bookshop” database

```sql
CREATE DATABASE bookshop;
USE bookshop;
```

![Screenshot 2023-01-21 at 8.10.43 PM.png](Lab%20Exercise%20Record%20deletion%20b2ea679b3d254006b9969096ae7ada71/Screenshot_2023-01-21_at_8.10.43_PM.png)

1. Create table `customers` based on the above image

```sql
CREATE TABLE customers (customer_id INT, customer_name VARCHAR(255), customer_address VARCHAR(255));
```

![Screenshot 2023-01-21 at 8.11.07 PM.png](Lab%20Exercise%20Record%20deletion%20b2ea679b3d254006b9969096ae7ada71/Screenshot_2023-01-21_at_8.11.07_PM.png)

1. Populate `customers` table

```sql
INSERT INTO customers (customer_id, customer_name, customer_address)
VALUES (1, 'Jack', '115 Old street Belfast'),
			 (2, 'James', '24 Carlson Rd London'),
       (4, 'Maria', '5 Fredrik Rd, Bedford'),
       (5, 'Jade', '10 Copland Ave Portsmouth '),
       (6, 'Yasmine', '15 Fredrik Rd, Bedford'),
       (3, 'Jimmy', '110 Copland Ave Portsmouth');
```

![Screenshot 2023-01-21 at 8.11.23 PM.png](Lab%20Exercise%20Record%20deletion%20b2ea679b3d254006b9969096ae7ada71/Screenshot_2023-01-21_at_8.11.23_PM.png)

![Screenshot 2023-01-21 at 8.11.39 PM.png](Lab%20Exercise%20Record%20deletion%20b2ea679b3d254006b9969096ae7ada71/Screenshot_2023-01-21_at_8.11.39_PM.png)

1. Remove customer record of Jimmy with ID number 3

```sql
DELETE FROM customers WHERE customer_id = 3;
```

![Screenshot 2023-01-21 at 8.11.55 PM.png](Lab%20Exercise%20Record%20deletion%20b2ea679b3d254006b9969096ae7ada71/Screenshot_2023-01-21_at_8.11.55_PM.png)