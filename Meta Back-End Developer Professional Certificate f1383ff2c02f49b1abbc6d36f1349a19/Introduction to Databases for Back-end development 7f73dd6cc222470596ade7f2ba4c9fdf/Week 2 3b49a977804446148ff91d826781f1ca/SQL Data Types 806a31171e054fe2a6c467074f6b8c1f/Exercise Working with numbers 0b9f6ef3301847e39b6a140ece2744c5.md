# Exercise: Working with numbers

| Stock table |
| --- |
| Device ID |
| 1 |
| 2 |

**Goal**

The goal of this exercise is for you to learn how to work with numerical values in a database. The objective of the exercise is that you will be able to demonstrate how to work with numerical data types in SQL. In this exercise, you will learn about two main variations of numeric data types.

**Scenario**

Mr. Carl Merkel owns a small business named CM Mobiles that sells mobile devices. He wants to create a database to store key information about mobile devices. This information includes: 

- The device ID or number
- The device name
- And the price of the device.

This information is displayed in the following table:

| Mobile Devices Table |  |  |
| --- | --- | --- |
| Device ID | Device name | Price |
| 1 | iPhone XR 1  | 1500.50  |
| 2 | Samsung SX  | 1200.50  |
| 3 | Nokia 730  | 1050.00  |

# Instructions

**Task 1: Create a database called cm_devices**

```sql
CREATE DATABASE cm_devices;
```

Make sure you select the database you want to create the table inside of by typing the following SQL statement:

```sql
USE cm_devices;
```

![Screenshot 2023-01-21 at 11.09.46 AM.png](Exercise%20Working%20with%20numbers%200b9f6ef3301847e39b6a140ece2744c5/Screenshot_2023-01-21_at_11.09.46_AM.png)

**Task 2: Create a SQL statement with relevant attributes and data types**

```sql
CREATE TABLE devices(deviceID int, deviceName varchar(50), price decimal);
```

```sql
SHOW tables;
```

![Screenshot 2023-01-21 at 11.11.21 AM.png](Exercise%20Working%20with%20numbers%200b9f6ef3301847e39b6a140ece2744c5/Screenshot_2023-01-21_at_11.11.21_AM.png)

```sql
SHOW columns from devices;
```

![Screenshot 2023-01-21 at 11.11.58 AM.png](Exercise%20Working%20with%20numbers%200b9f6ef3301847e39b6a140ece2744c5/Screenshot_2023-01-21_at_11.11.58_AM.png)

### Task 3: Create Stock table

Mr. Merkel wants to create another basic table in the database to store data about the stock of the devices including device ID, quantity available in the stock and total available cost of the quantity. This basic table is shown in the table below, with each column showing device ID, the quanity in stock and the total price.

| Stock table |  |  |
| --- | --- | --- |
| Device ID | Quantity   | Total price   |
| 1  | 5  | 5000.75  |
| 2  | 3  | 3500.50  |

Based on the table and information above, complete the following:

**1.**	Identify an appropriate table name to create, given the information provided.

**2.**	Identify columns that should be available in this table and define them with the appropriate data types.

**3.**	Write the full SQL statement that creates the table and columns.

### Solution

```sql
CREATE TABLE Stock(deviceID int, quantity int, totalPrice decimal);
```