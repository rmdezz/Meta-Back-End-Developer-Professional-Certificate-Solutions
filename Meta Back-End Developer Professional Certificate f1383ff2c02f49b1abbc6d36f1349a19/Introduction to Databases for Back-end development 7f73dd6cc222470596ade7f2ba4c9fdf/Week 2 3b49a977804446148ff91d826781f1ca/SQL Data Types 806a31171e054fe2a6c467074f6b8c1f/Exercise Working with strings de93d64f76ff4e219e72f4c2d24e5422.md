# Exercise: Working with strings

# **Goal**

The goal of this exercise is for you to learn how to work with string values in a database. The objective is to allow you to practice working with string data types in SQL. This exercise focuses on the two most used string datatypes in SQL: CHAR and VARCHAR.

# **Scenario**

Mr. Carl Merkel owns a small business that sells mobile devices called “CM Mobiles”. He wants to create a new table to store key information about customers including customer username, customer full name and customer email address as shown in the following table of data.

### **Customer Table:**

| username | Full Name | Email |
| --- | --- | --- |
| Custom001 | John Johnson | J.Johnson@email.com |
| Custom002 | Carl Schmidt | Carl.Schmidt@email.com |
| Custom003 | Yara Suliman | Yara.Suliman@email.com |

# **Instructions**

Please attempt the below tasks before you continue, so you can check and compare your answers with our solution.

Create a SQL statement with relevant attributes and data types as follows:

**1.**      Identify a suitable name for the table in which you want to store data about mobile devices.

**2.**      Identify the data type for each column of the table.

**3.**      Write a complete SQL statement to create the table inside the cm_devices database.

# Solution

1. Create and use the database “cm_devices”:

```sql
CREATE DATABASE cm_devices;
USE cm_devices;
```

1. Create the customer table:

```sql
CREATE TABLE customer(username char(9), fullName varchar(100), email varchar(255));
SHOW tables;
show columns from customer;
```

![Screenshot 2023-01-21 at 12.08.18 PM.png](Exercise%20Working%20with%20strings%20de93d64f76ff4e219e72f4c2d24e5422/Screenshot_2023-01-21_at_12.08.18_PM.png)

# Additional task

Mr. Carl Merkel wants to create another basic table in the cm_devices database to store the customers' feedback. This table must include three columns:

- Feedback ID column,
- Feedback type column with a maximum of 100 characters,
- A comment column with a maximum of 500 characters.

The **feedback table** is illustrated below.

| Feedback ID | Feedback type | Feedback comment |
| --- | --- | --- |
| Feed0001 | Good | It is a very good product but the delivery was not great. |
| Feed0002 | Very good | No comment |

You are required to complete the following tasks:

A. Declare the columns with the right data type for each.

B. Write the SQL statement that creates the feedback table.

## Solution

1. Create table “feedback” with the requirements:

```sql
CREATE TABLE feedback(feedbackID char(8), category varchar(100), comment text(500);
show tables;
show columns from feedback;
```

![Screenshot 2023-01-21 at 12.11.54 PM.png](Exercise%20Working%20with%20strings%20de93d64f76ff4e219e72f4c2d24e5422/Screenshot_2023-01-21_at_12.11.54_PM.png)