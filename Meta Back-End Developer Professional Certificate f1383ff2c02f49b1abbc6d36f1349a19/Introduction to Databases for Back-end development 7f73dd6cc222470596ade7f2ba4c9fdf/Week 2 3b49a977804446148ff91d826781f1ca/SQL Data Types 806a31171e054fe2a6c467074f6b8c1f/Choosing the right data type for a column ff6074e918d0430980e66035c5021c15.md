# Choosing the right data type for a column

# **Goal**

Practice how to choose suitable data types for different kinds of columns in the table

# **Exercise objectives**

This exercise demonstrates how to choose suitable data types for a variety of columns to store data as string, integer, date and decimal values.

# **Scenario**

Mr. Carl Merkel owns a small business that sells mobile devices called “CM Mobiles” in Harrow town near London. He wants to create a database to store key information about customers’ orders in order to generate invoices for his customers including customer name, order date, quantity and total price. This data can be seen in the following invoice table:

| Invoice Table |  |  |  |
| --- | --- | --- | --- |
| Customer name | Order Date | Product Quantity | Total price |
| Mark Dani | 25/03/2022  | 5  | 750.50  |
| Karl Masonry  | 22/03/2022  | 4  | 600.75  |
| Jack Raymond  | 20/03/2022  | 3  | 978.00  |

# Solution

1. Create database “cm_devices”:

```sql
CREATE DATABASE cm_devices;
USE cm_devices;
```

1. Create table “invoice” satisfying the requirements:

```sql
CREATE TABLE invoice (customer_name varchar(255), order_date date, quantity int, total_price decimal);
```

# Additional task

Mr. Carl needs to have a new table to store the contact details of each customer including customer account number, customer phone number and customer email address.

You are required to choose a relevant data type for each of the columns.

## Solution

- customer account number: int
- phone number: int
- email address: varchar(255)

```sql
CREATE TABLE customer (account_number int, phone_number int, email_address varchar(255));
```