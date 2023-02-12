# How is data related?

# Introduction

The text describes the process of establishing relationships between data in a database, using the example of an online store. It explains that data stored in a database cannot exist in isolation and must have a relationship with other data to be processed into meaningful information.

# Background

![Untitled](How%20is%20data%20related%20daa9ee49eaa5471a890571c97c5cb9a3/Untitled.png)

- A database table is a collection of related data entries and it consists of rows and columns. Each row represents a single record, and each column represents a field for that record.
- A primary key is a field in a table, which uniquely identifies each record/row in a database table. It cannot contain null values and must be unique.

![Untitled](How%20is%20data%20related%20daa9ee49eaa5471a890571c97c5cb9a3/Untitled%201.png)

- A foreign key is a field in one table that is primary key in another table. It is used to establish a link between the data in two tables.
- Relational database management systems (RDBMS) are the most widely used type of database management system, which are based on the relational model.

# Example

Using the example of an online store, the text explains how the database establishes a link between the data in the order table and the customer table by using fields such as the primary key and foreign key.

| Order table |  |  |  |
| --- | --- | --- | --- |
| Order ID | Customer ID | Product | Quantity |
| O1 | C1 | P1 | 1 |
| O2 | C2 | P2 | 5 |
| O3 | C1 | P3 | 10 |

| Customer Table |  |  |  |
| --- | --- | --- | --- |
| Customer ID | First Name | Last Name | Email |
| C1 | Sarah | Hogan | xxx |
| C2 | John | Smith | yyy |
- In this example, the primary key in the Order table is the Order ID and the foreign key is the Customer ID.
- The primary key in the Customer table is the Customer ID.
- By linking the Customer ID in the Order table with the primary key in the Customer table, the database can retrieve data from both tables in a meaningful way.

# Other examples

- A library database can have tables for books, authors, and borrowers, where primary key in the books table is ISBN, and the foreign key in the borrowers table is ISBN, linking the books borrowed by a borrower.

| Books Table |  |  |
| --- | --- | --- |
| ISBN | Title | Author |
| B1 | T1 | A1 |
| B2 | T2 | A2 |
| B3 | T3 | A3 |

| Borrowers Table |  |  |
| --- | --- | --- |
| Borrower ID | Name | ISBN |
| 1 | N1 | B1 |
| 2 | N2 | B2 |
- A school database can have tables for students, classes, and teachers, where primary key in the students table is a student ID, and the foreign key in the classes table are student ID, teacher ID and subject ID linking the classes taken by a student.

| Students Table |  |  |
| --- | --- | --- |
| Student ID | Name | Age |
| S1 | N1 | 18 |
| S2 | N2 | 19 |
| S3 | N3 | 20 |

| Classes Table |  |  |  |
| --- | --- | --- | --- |
| Class ID | Student ID | Teacher | Subject |
| C1 | S1 | T1 | M |
| C2 | S2 | T2 | S |
| C3 | S1 | T3 | E |

| Teacher Table |  |
| --- | --- |
| Teacher ID | Name |
| T1 | N1 |
| T2 | N2 |
| T3 | N3 |

| Subject Table |  |
| --- | --- |
| Subject ID | Name |
| M | Math |
| S | Science |
| E | Economics |

In a real-world scenario, the teacher and the subject would likely have their own tables in the database, and the class table would include foreign keys for the teacher and the subject. The foreign keys would link to the primary keys in the teacher and subject tables, respectively.

By linking the foreign keys Teacher ID and Subject ID in the Classes table with the primary key in the Teacher and Subject tables, respectively, the database can retrieve data from all three tables in a meaningful way. This allows for a more detailed and accurate representation of the data in the classes.