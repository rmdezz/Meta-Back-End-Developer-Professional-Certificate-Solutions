# ORDER BY and WHERE

# **Goal**

The goal of this exercise is for you to learn how to use the SQL ORDER BY and WHERE clauses to sort and filter data.

# **Objectives**

1. Use the SQL ORDER BY clause to sort the result of a query

2. Use the SQL WHERE clause to specify a condition for records filtering

# **The chinook database example**

In this exercise we are going to consider the well-known “chinook sample” database, which is widely used for demos and testing purposes. Also, it has been implemented in coursera platform, which is good to be familiar with as you are going to use it to complete this exercise.

The chinook sample database consists of the following database schema.

![Untitled](ORDER%20BY%20and%20WHERE%204e0fde875a874704a91ef52518346f49/Untitled.png)

# **Before you start:**

To complete this exercise you need to do the following steps first to setup the Chinook database and create the Customer table.

1. Create the chinook database and use it in MySQL terminal.

```sql
**CREATE DATABASE Chinook;
USE Chinook;**
```

2. Create the customer table as follows (Copy and paste the code in the terminal):

```sql
**CREATE TABLE Customer (CustomerId INT NOT NULL, FirstName VARCHAR(40) NOT NULL, LastName VARCHAR(20) NOT NULL, Company VARCHAR(80), Address VARCHAR(70), City VARCHAR(40), State VARCHAR(40), Country VARCHAR(40), PostalCode VARCHAR(10), Phone VARCHAR(24), Fax VARCHAR(24), Email VARCHAR(60) NOT NULL, SupportRepId INT, CONSTRAINT PK_Customer PRIMARY KEY (CustomerId));**
```

3. Insert the following records of data into the Customer table (Copy and paste code into the terminal):

```sql
**INSERT INTO Customer (CustomerId, FirstName, LastName, Company, Address, City, State, Country, PostalCode, Phone, Fax, Email, SupportRepId) VALUES (1, 'Luís', 'Gonçalves', 'Embraer - Empresa Brasileira de Aeronáutica S.A.', 'Av. Brigadeiro Faria Lima, 2170', 'São José dos Campos', 'SP', 'Brazil', '12227-000', '+55 (12) 3923-5555', '+55 (12) 3923-5566', 'luisg@embraer.com.br', 3);**

**INSERT INTO Customer (CustomerId, FirstName, LastName, Company, Address, City, State, Country, PostalCode, Phone, Fax, Email, SupportRepId) VALUES (2, 'Eduardo', 'Martins', 'Woodstock Discos', 'Rua Dr. Falcão Filho, 155', 'São Paulo', 'SP', 'Brazil', '01007-010', '+55 (11) 3033-5446', '+55 (11) 3033-4564', 'eduardo@woodstock.com.br', 4);

INSERT INTO Customer (CustomerId, FirstName, LastName, Company, Address, City, State, Country, PostalCode, Phone, Fax, Email, SupportRepId) VALUES
(3, 'Alexandre', 'Rocha', 'Banco do Brasil S.A.', 'Av. Paulista, 2022', 'São Paulo', 'SP', 'Brazil', '01310-200', '+55 (11) 3055-3278', '+55 (11) 3055-8131', 'alero@uol.com.br', 5);INSERT INTO Customer (CustomerId, FirstName, LastName, Company, Address, City, State, Country, PostalCode, Phone, Fax, Email, SupportRepId) VALUES
(4, 'Roberto', 'Almeida', 'Riotur', 'Praça Pio X, 119', 'Rio de Janeiro', 'RJ', 'Brazil', '20040-020', '+55 (21) 2271-7000', '+55 (21) 2271-7070', 'roberto.almeida@riotur.gov.br', 3);

INSERT INTO Customer (CustomerId, FirstName, LastName, Company, Address, City, State, Country, PostalCode, Phone, Fax, Email, SupportRepId) VALUES (5, 'Mark', 'Philips', 'Telus', '8210 111 ST NW', 'Edmonton', 'AB', 'Canada', 'T6G 2C7', '+1 (780) 434-4554', '+1 (780) 434-5565', 'mphilips12@shaw.ca', 5);**

I**NSERT INTO Customer (CustomerId, FirstName, LastName, Company, Address, City, State, Country, PostalCode, Phone, Fax, Email, SupportRepId) VALUES (6, 'Jennifer', 'Peterson', 'Rogers Canada', '700 W Pender Street', 'Vancouver', 'BC', 'Canada', 'V6C 1G8', '+1 (604) 688-2255', '+1 (604) 688-8756', 'jenniferp@rogers.ca', 3);**
```

# **Instructions**

Please attempt the following tasks before you continue, so that you can check and compare your answers with our solution.

Task 1: Write a SQL statement to display all data existing in the customer table.

Task 2: Write a SQL statement to sort the result set in ascending order by first name.

Task 3: Filter the result set data based on a condition where country = France.

# Solution

### Task 1

```sql
SELECT * FROM Customer;
SELECT CustomerID, FirstName, LastName, City, State, Country FROM Customer;
```

![Untitled](ORDER%20BY%20and%20WHERE%204e0fde875a874704a91ef52518346f49/Untitled%201.png)

You will now see loads of data about customers displayed on the screen, which makes it hard to find relevant data about specific customers.

### Task 2

```sql
SELECT CustomerID, FirstName, LastName, City, State, Country FROM Customer ORDER BY FirstName ASC;
```

![Screenshot 2023-01-21 at 11.57.52 PM.png](ORDER%20BY%20and%20WHERE%204e0fde875a874704a91ef52518346f49/Screenshot_2023-01-21_at_11.57.52_PM.png)

### Task 3

```sql
SELECT CustomerID, FirstName, LastName, City, State, Country FROM Customer WHERE Country = "Canada";
```

![Screenshot 2023-01-21 at 11.58.28 PM.png](ORDER%20BY%20and%20WHERE%204e0fde875a874704a91ef52518346f49/Screenshot_2023-01-21_at_11.58.28_PM.png)