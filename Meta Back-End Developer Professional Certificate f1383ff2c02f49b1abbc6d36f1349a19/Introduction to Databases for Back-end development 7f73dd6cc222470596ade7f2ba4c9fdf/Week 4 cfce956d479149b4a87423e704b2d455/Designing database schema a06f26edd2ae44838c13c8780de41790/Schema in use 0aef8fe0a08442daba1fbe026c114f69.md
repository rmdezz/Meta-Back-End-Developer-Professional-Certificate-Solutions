# Schema in use

Creating a database schema is an important step in building a database management system. In this tutorial, we will walk you through the process of creating a simple database schema using SQL and MySQL. We will be building the schema for a shopping cart database consisting of three tables: customer, product, and cart order.

First, we need to create a new database called "shopping cart_db". We do this by using the SQL command:

```sql
CREATE DATABASE shopping_cart_db;
```

Now that we have created the database, we can move on to creating the tables.

## Table 1: Customer

The first table we will create is the "customer" table, which will store information about each customer, such as customer ID, name, address, email, and phone number. We use the SQL command:

```sql
CREATE TABLE customer (
customer_id INT PRIMARY KEY,
name VARCHAR(100),
address VARCHAR(255),
email VARCHAR(100),
phone VARCHAR(10)
);
```

Here, we use the **`CREATE TABLE`** command, followed by the name of the table, "customer". In the parentheses, we specify the fields and their data types. The **`customer_id`** field is an integer and is designated as the primary key for the table using the **`PRIMARY KEY`** keyword.

## Table 2: Product

The next table we will create is the "product" table, which will store information about each product, such as product ID, name, price, and description. We use the SQL command:

```sql
CREATE TABLE product (
product_id INT PRIMARY KEY,
name VARCHAR(100),
price NUMERIC(8,2),
description VARCHAR(255)
);
```

This table is created in the same way as the "customer" table, with the **`product_id`** field being designated as the primary key.

## Table 3: Cart Order

The final table we will create is the "cart_order" table, which will store information about each cart order, such as order ID, customer ID, product ID, quantity, order date, and status. We use the SQL command:

```sql
CREATE TABLE cart_order (
order_id INT PRIMARY KEY,
customer_id INT,
product_id INT,
quantity INT,
order_date DATE,
status VARCHAR(100),
FOREIGN KEY (customer_id) REFERENCES customer(customer_id),
FOREIGN KEY (product_id) REFERENCES product(product_id)
);
```

This table also includes two foreign keys, "customer_id" and "product_id", which link the data in the cart_order table to the corresponding data in the customer and product tables. 

This relationship is established through primary and foreign keys. A primary key is a unique identifier for each record in a table. A foreign key is a field in one table that refers to the primary key of another table. In this case, the foreign keys in the cart_order table refer to the primary keys in the customer and product tables.

In this tutorial, we have shown you how to create a simple database schema for a shopping cart database using SQL and MySQL. This process can be applied to create schemas for other databases as well.

### Note

- Note: The code and examples provided above are for demonstration purposes only and may not work as is when executed on a specific DBMS or platform.
- It's important to understand the specific syntax and commands for the platform or software you're working with.
- Additionally, when creating a real-world database schema, it's important to keep in mind the purpose and requirements of the database, as well as best practices for data integrity, security, and performance.