# Working with default values

# **Goal**

The goal of this exercise is for you to learn how to work with default values in a database. The objective is to allow you to practice working with default values using the default constraint in SQL.

# **Scenario**

Mr. Carl Merkel owns a small business that sells mobile devices called “CM Mobiles” in Harrow, London. He wants to create a database to store key information about customers' addresses including customer ID, street, postcode and town name. The list of addresses for current customers of CM Mobiles is listed in the address table below.

| Address Table   |  |  |  |
| --- | --- | --- | --- |
| Customer ID | Street    | Postcode   | Town  |
| 1  | 10 Carsten Rd.  | HA3 0AE | Harrow  |
| 2   | 15 Denise Ave.  | HA3 0AE | Harrow  |
| 3   | 13 Merkel Ave.   | HA3 0AE | Harrow  |
| 4   | 12 Carsten Rd.  | HA3 0AE | Harrow  |
| 5   | 15 Hellen way   | HA3 0AE  | Harrow  |
| 6   | 13 Carsten Rd   | HA3 0AE  | Harrow  |
| 7    | 11 Malika Rd.   | NW9 0AX  | Kingsbury |

# **Instructions**

Create an SQL statement  with relevant attributes and constraints as follows:

**1.** Identify the column that requires default values.

**2.** Write a complete SQL statement to create the address table with relevant constraints.

Please attempt the tasks before you continue so you can check and compare your answers with the solution.

# Solution

1. Create database “cm_devices”:

```sql
CREATE DATABASE cm_devices;
USE cm_devices;
```

1. Create table “address”

```sql
CREATE TABLE address 
(customer_id int NOT NULL AUTO_INCREMENT, street VARCHAR(255) NOT NULL, postcode char(7) NOT NULL, town VARCHAR(100) DEFAULT 'Harrow', PRIMARY KEY (customer_id)
);
```

![Screenshot 2023-01-21 at 1.02.48 PM.png](Working%20with%20default%20values%20cc79648e29404c94a7ac07c24db74e38/Screenshot_2023-01-21_at_1.02.48_PM.png)

# Additional task

Mr. Carl Merkel notices that most customers come from the same postcode i.e., “HA97DE”.

You are required to write the SQL statement again to declare both the postcode and the town name with default values.

Remember to drop the address table before creating a new one.

To drop the table, simply type: 

```sql
DROP TABLE address;
```