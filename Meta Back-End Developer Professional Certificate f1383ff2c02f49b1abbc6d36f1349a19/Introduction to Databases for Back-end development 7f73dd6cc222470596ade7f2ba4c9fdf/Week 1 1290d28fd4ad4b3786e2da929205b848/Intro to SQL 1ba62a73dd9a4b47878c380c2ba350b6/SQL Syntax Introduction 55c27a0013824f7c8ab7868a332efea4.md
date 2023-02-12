# SQL Syntax Introduction

# Introduction

- SQL is a popular language choice for interacting with databases, because it offers several advantages such as being user-friendly, a standard language, portable, comprehensive, and efficient.
- In this text, you will learn how to create a database using the DDL subset of SQL, populate and modify data using the DML subset, and read and query data using the DQL subset.

# Creating a database

- The first step is to create the database using the SQL DDL subset. The syntax is "create database" followed by the name of the database and a semicolon at the end of the statement.

```sql
CREATE DATABASE [NAME OF DATABASE];
```

## Example

To create the “college” database, you would do the following:

```sql
CREATE DATABASE college;
```

Once the database is created, you can create tables using the "create table" syntax followed by the table name.

```sql
CREATE TABLE [TABLE NAME];
```

# Populating and Modifying Data

The next step is to populate the tables with data using the DML subset of SQL. 

## Add data

The syntax to add data to a table is "INSERT INTO" followed by the table name, a list of required columns within parentheses, the keyword "VALUES" and the values for each of the fields.

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

### Example

For example, to add data to the "student" table in the "college" database, you would use the following syntax:

```sql
INSERT INTO student (ID, first_name, last_name, date_birth)
VALUES (1, "John", "Doe", "01-01-1990);
```

## Update data

To update or modify data, you would use the "UPDATE" syntax, followed by the table name, the keyword "SET" and the columns and values to update, and a condition “WHERE” to filter the records you want to update.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### Example

For example, to change the date of birth for the student with ID 2, you would use the following syntax:

```sql
UPDATE student
SET date_birth = "01-01-1991"
WHERE ID = 2;
```

## Delete data

To delete data, the command would be "DELETE FROM" followed by the table name and a "WHERE" clause to specify which record(s) to delete.

```sql
DELETE FROM table_name 
WHERE condition;
```

### Example

to delete the data for the student with ID 3 from the "student" table, you would use the following syntax:

```sql
DELETE FROM student
WHERE ID = 3;
```

# Reading and Querying Data

To read and query data within a database, you would use the DQL subset of SQL, specifically the "select" command. The syntax for the "select" command is "select" followed by the columns you want to retrieve, "from" followed by the table name, and an optional "where" clause to filter the records based on a certain condition.

```sql
SELECT column1, column2, ...
FROM table_name;
```

For example, to retrieve the first name and last name of all students in the "student" table, you would use the syntax

```sql
SELECT first_name, last_name
FROM student;
```

If you wanted to retrieve the same information but only for students with a certain ID, you would add a "where" clause to filter the records, like:

```sql
SELECT first_name, last_name
FROM student
WHERE ID = 2;
```

# Conclusion

Overall, by mastering SQL and its subsets, you can interact with databases, create and modify databases, tables and data within them, and retrieve and query data in a quick and efficient manner. With this knowledge, you can become a proficient data engineer and take your skills to the next level.