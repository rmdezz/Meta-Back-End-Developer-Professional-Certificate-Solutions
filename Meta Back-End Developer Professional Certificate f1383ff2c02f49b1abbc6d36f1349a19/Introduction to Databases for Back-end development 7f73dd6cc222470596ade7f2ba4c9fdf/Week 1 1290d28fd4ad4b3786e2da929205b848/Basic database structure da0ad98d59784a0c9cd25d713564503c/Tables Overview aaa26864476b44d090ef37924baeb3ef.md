# Tables Overview

In this reading, you will learn about tables in a relational database, including their structure, data types, and the role of primary and foreign keys.

# Table Structure

A table in a database is the most basic type of database object and is responsible for storing data. Like any table, a database table also consists of rows and columns. The rows run horizontally, representing each record, while the columns run vertically, defining each field. Each column has a name that describes the data that is stored in it. 

## Example

For example, in a student table, the columns may include student ID, first name, last name, date of birth, home address, and faculty.

| Student table |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- |
| ID | First Name | Last Name | Date of Birth | Home Address | Faculty |

![[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview)](Tables%20Overview%20aaa26864476b44d090ef37924baeb3ef/Untitled.png)

[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview)

- There are also six rows within this table; one for each student. In other words, the table contains the records of six students.
- Each cell in a row or record contains a piece of data such as student ID = 1, first name = Emily, last name = Williams and so on.
- The student ID would probably have a data type of INT, for example. First name and last name would have a data type of VARCHAR and date of birth would have a data type of DATE.

# Data types

Every column in a table has a data type, which is defined by SQL. A data type defines the type of value that can be stored in a table column. 

## Example

Some examples of data types include:

- Numeric data types: INT, TINYINT, BIGINT, FLOAT, and REAL.
- Date and time data types: DATE, TIME, and DATETIME.
- Character and string data types such as CHAR and VARCHAR.
- Binary data types such as BINARY and VARBINARY.

There are also miscellaneous data types such as:

- Character Large Object (CLOB) for storing large blocks of text
- Binary Large Object (BLOB) for storing binary data such as images.

# Tables in a relational database

In a relational database, there are multiple tables that represent the structure of the software system. These tables may include Student, Teacher, Class, and Subject. In relational database terminology, a table is also known as a relation. A table row or record is also known as a tuple. Each table or relation in a database has its own schema, which is the structure of the table and includes the name of the table, its attributes, their names, and data types.

# Primary Key

In a table, there is a field or column that is known as a key that can uniquely identify a particular tuple or row in a relation or table. This key is specifically known as a primary key. For example, in the student table, the student ID allows you to uniquely identify a particular row. Other columns, such as first name, last name, and date of birth, may not be unique.

## Composite Primary Key

In some cases, the primary key can comprise more than one column or field. This happens when a single column cannot make a record in a table uniquely identifiable. 

For example, in the table below, the EMP_ID values aren’t unique, so the column is not unique by itself. Thus, this column alone cannot be used as the primary key of this table. However, the EMP_ID and DEPT_ID columns together can make a record unique. Therefore, the primary key of this table is EMP_ID and DEPT_ID. This is also known as a composite primary key.

![[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview)](Tables%20Overview%20aaa26864476b44d090ef37924baeb3ef/Untitled%201.png)

[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/UjZNO/tables-overview)

# Foreign Key

A foreign key is a column or set of columns in a table that is used to establish and maintain a link between the data in two tables. It is used to reference a primary key in another table. For example, in a student table and a class table, the foreign key would be the class ID in the student table, which references the primary key of the class table.

![Untitled](Tables%20Overview%20aaa26864476b44d090ef37924baeb3ef/Untitled%202.png)

# Integrity Constraints

One important aspect of tables is integrity constraints, which are rules or constraints that a table must abide by.

There are three main integrity constraints:

1. Key constraints

2. Domain constraints

3. Referential integrity constraints

## Key Constraints

A key constraint specifies that there should be a column, or columns, in a table that can be used to fetch data for any row. 

This key attribute or primary key should never be NULL or the same for two different rows of data. The primary key is used to uniquely identify a row in a table, like in the example of student table where student ID can be used to fetch data for each of the students.

## Domain Constraints

Domain constraints refer to the rules defined for the values that can be stored for a certain column. For instance, you cannot store the home address of a student in the first name column. Similarly, a contact number cannot exceed ten digits. These constraints are put in place to make sure the data stored in the table is consistent and adheres to certain rules.

## Referential Integrity Constraints

When a table is related to another table via a foreign key column, then the referenced column value must exist in the other table. This means that values should exist in the foreign key column in the table that is referencing to another table. This ensures the consistency of data and relationship between tables.

# Conclusion

By the end of this reading, you should have a deeper understanding of tables in a relational database and how data is structured and organized within them. Additionally, you should have a good understanding of integrity constraints, primary and foreign keys.