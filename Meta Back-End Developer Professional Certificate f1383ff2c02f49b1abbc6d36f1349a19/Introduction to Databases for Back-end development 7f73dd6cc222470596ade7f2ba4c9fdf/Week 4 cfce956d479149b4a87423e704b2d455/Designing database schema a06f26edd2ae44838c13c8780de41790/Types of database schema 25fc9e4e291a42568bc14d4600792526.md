# Types of database schema

When designing a database, it's important to understand the different types of database schemas that are available to you. In this tutorial, we will explore the concepts of logical and physical database schemas, and show how they can be applied in practice using MySQL as an example.

# Logical Database Schema

A logical database schema is a representation of how data is organized in terms of tables and attributes. It defines the relationships between different tables in a database and illustrates how the data is linked together. This is often achieved through Entity-Relationship (ER) modeling.

![Untitled](Types%20of%20database%20schema%2025fc9e4e291a42568bc14d4600792526/Untitled.png)

### Example

- For example, a simple ER model for an ordering application might show the relationship between an order, the shipment in which it will be shipped, and the courier assigned to it. In this model, the ID attribute in each table serves as a primary key, providing a unique identifier for each record. The shipment ID and courier ID attributes in the order table are foreign keys, linking the order data with the shipment and courier data.

![Screenshot 2023-01-22 at 2.59.47 PM.png](Types%20of%20database%20schema%2025fc9e4e291a42568bc14d4600792526/Screenshot_2023-01-22_at_2.59.47_PM.png)

- Here’s another example:

| Customers table |  |  |
| --- | --- | --- |
| CustomerID | FirstName | LastName |
| 1 | John | Smith |
| 2 | Emily | Williams |
| 3 | Michael | Brown |

| Products table |  |  |
| --- | --- | --- |
| ProductID | ProductName | Price |
| 1 | iPhone | 799 |
| 2 | Samsung Galaxy | 499 |
| 3 | Google Pixel | 699 |

| Orders table |  |  |
| --- | --- | --- |
| OrderID | CustomerID | ProductID |
| 1 | 1 | 1 |
| 2 | 2 | 2 |
| 3 | 3 | 3 |

In this example, the Customers table has a `primary key` called "CustomerID" and contains information about customers such as their first and last names. The Products table has a `primary key` called "ProductID" and contains information about products such as the product name and price. The Orders table has a `primary key` called "OrderID" and contains information about orders such as the "CustomerID" and "ProductID” (foreign keys).

# Physical Database Schema

A physical database schema, on the other hand, is a representation of how data is stored on disk. It defines the actual structure of the database, including the tables and other objects, and is typically implemented using SQL commands.

For example, to create a physical schema for an online store database, one could use SQL statements to create tables for customers, products, and transactions. The exact syntax of these statements may vary between different database systems, but the overall process is generally the same.

Here is an example of a physical database schema:

```sql
CREATE TABLE Customers (
    CustomerID INT NOT NULL PRIMARY KEY,
    FirstName VARCHAR(255) NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    Email VARCHAR(255) NOT NULL UNIQUE
);

CREATE TABLE Products (
    ProductID INT NOT NULL PRIMARY KEY,
    ProductName VARCHAR(255) NOT NULL,
    Description TEXT NOT NULL,
    Price DECIMAL(10,2) NOT NULL
);

CREATE TABLE Orders (
    OrderID INT NOT NULL PRIMARY KEY,
    CustomerID INT NOT NULL,
    ProductID INT NOT NULL,
    Quantity INT NOT NULL,
    OrderDate DATE NOT NULL,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID),
    FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
);
```

In this example, the Customers table is created with the SQL command **`CREATE TABLE`**
, the table name is "Customers" and its columns are defined inside the parentheses. The **`CustomerID`** column is an integer data type and is set as the primary key of the table. the **`FirstName`**,**`LastName`** and **`Email`** columns are varchar data type and the email column has a unique constraint.

Similarly, the Products table is created with the SQL command `CREATE TABLE`, the table name is "Products" and its columns are defined inside the parentheses. The `ProductID`column is an integer data type and is set as the primary key of the table. the `ProductName` and `Description`columns are varchar and text data type, respectively. The price is a decimal data type. Finally, the Orders table is created in the same way as the other two tables, and it has columns to store the `OrderID`, `CustomerID`, `ProductID`, `Quantity`, `OrderDate`, and also include the foreign key constraint where **`CustomerID`** references to the **`CustomerID`** column in the Customers table, and **`ProductID`** references to the **`ProductID`** column in the Products table.

This establishes the relationship between the Orders table and the Customers and Products table, enabling the database to ensure referential integrity. This is the complete example of physical database schema and this is the SQL commands needed to create the physical structure of the database, the physical schema can be more complex depending on the complexity of the database.

# Summary

In summary, **logical database schemas** provide a representation of how data is organized in terms of tables and relationships, **while physical database schemas** define how data is stored on disk. Understanding the distinction between these two types of schemas is important when creating and designing a database. Additionally, it is important to note that the actual implementation of a physical schema with SQL statements could differ slightly between different database systems.