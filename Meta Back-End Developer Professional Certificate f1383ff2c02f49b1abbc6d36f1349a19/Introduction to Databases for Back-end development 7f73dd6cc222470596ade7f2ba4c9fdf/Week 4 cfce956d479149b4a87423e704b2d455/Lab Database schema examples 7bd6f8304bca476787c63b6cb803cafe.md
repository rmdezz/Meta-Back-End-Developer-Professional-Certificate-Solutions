# Lab: Database schema examples

# **Goal**

Introduce an example of a database schema to demonstrate how data can be organized and related in tables.

# **Objectives**

Understand how to design a database schema

# **The chinook database example**

This exercise uses the well-known “chinook sample” database, which is widely used for example relational database demos and testing purposes. Also, it has been implemented in Coursera platform, which is good to be familiar with as well.

However, you are going to focus only on some of the main tables introduced in this database to highlight how a database schema is designed, and not the entire chinook schema.

# **Database schema design**

Before you develop your actual database, you should design a relevant database schema to document the requirements and to propose an architecture of the database structure. To design a basic database schema, you need to apply the following steps:

Step 1: Define the database purpose.

Step 2: Identify the database tables including

- Tables attributes
- Attributes data types
- Primary key for each table

Step 3: Create relationships between tables

# **Instructions**

Please attempt the following tasks before you continue, so that you can check and compare your answers with the solution.

Task 1: Identify the database purposes.

Task 2: Identify 6 main tables with a brief description and a primary key for each table.

Task 3: Identify the relationships between the 6 main tables.

Task 4: Create an entity relationship diagram of the 6 main tables.

## **Task 1: Identify the database purpose**

The “chinook sample” database represents a fictitious digital media company that includes information about artists, albums, media tracks, invoices and customers.

## **Task 2: Identify the database tables**

The chinook sample database has considered adequate normalization level and created 11 tables to store and relate data to avoid data redundancy. However, this exercise will only focus on 6 main tables, including some relevant attributes for each.

| Table name | Description | Diagram |
| --- | --- | --- |
| Employees | The employee table stores the data of all employees. 

The diagram presents 8 attributes with relevant datatypes.

Employee ID is the primary key in this table. |  1 |
| Customers | The customer table stores customers data. 

In the diagram, 8 attributes with relevant datatypes are presented. 

Customer ID is the primary key in this table. |  2 |
| Invoices | The invoice table stores data on invoices.
 
In the diagram, 5 attributes with relevant datatypes are presented. 

Invoice ID is the primary key in this table. |  3 |
| Artists | The artist table stores data on artists. 

Only 2 attributes, the artist ID and artist name, are presented in the diagram alongside their relevant data types.

Artists ID is the primary key in this table. | 4
 |
| Albums | The album table stores data about a list of tracks. 

In the diagram, 3 attributes with relevant data types are presented. 

Album ID is the primary key in this table.
 | 5
 |
| Tracks | The tracks table stores the data of songs. 

In the diagram there are 5 attributes with relevant data types. 

Tracks ID is the primary key in this table.

 
 | 6
 |

### Diagram 1

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled.png)

### Diagram 2

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%201.png)

### Diagram 3

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%202.png)

### Diagram 4

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%203.png)

### Diagram 5

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%204.png)

### Diagram 6

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%205.png)

## **Task 3: Identify relationships between tables**

The chinook sample database defines the following relationships between the 6 stated tables:

- Each employee will support one or many customers.
- Each customer may have multiple invoices
- Each track belongs to one album.
- Each invoice relates to one track.
- Each track belongs to one album
- Each album may contain multiple tracks
- Each artist has one or multiple albums

## **Task 4: Create entity relationship diagram**

The final diagram connects all tables by using the FOREIGN KEYS as illustrated in the following diagram. Remember this is just a customized part of the chinook database schema. If you want to see the entire diagram you can check Appendix A.

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%206.png)

## **Additional task** **(optional)**

You are required to extend the customized chinook schema by adding a new table called "location" that shows the city and the country the artist lives in.

**Solution**

- Add a new table called location
- Add a foreign key “locationId” to the “Artists” table to connect it with the location table
- The new chinook customized schema must look like the following ER-diagram:

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%207.png)

## **Appendix A: the original Chinook database schema**

The following diagram is a blueprint of the chinook database schema that shows how data is organized and related in tables.

![Untitled](Lab%20Database%20schema%20examples%207bd6f8304bca476787c63b6cb803cafe/Untitled%208.png)