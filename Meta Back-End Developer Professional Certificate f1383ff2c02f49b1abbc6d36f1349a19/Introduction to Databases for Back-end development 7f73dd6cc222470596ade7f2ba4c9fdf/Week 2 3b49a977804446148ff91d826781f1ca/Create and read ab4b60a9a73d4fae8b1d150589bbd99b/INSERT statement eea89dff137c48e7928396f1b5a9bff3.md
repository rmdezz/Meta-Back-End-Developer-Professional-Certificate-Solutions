# INSERT statement

# Introduction

The Insert statement in SQL is used to add new rows and columns to existing tables or even create new tables from scratch. 

The insert statement is written using the Insert into clause, followed by the name of the table and then a list of columns contained within a pair of parentheses and separated by commas. Then the values keyword is used to add a list of values within a pair of parenthesis. It's important to remember that each value corresponds to a specific column and should reflect the same data type and order.

# Example

To illustrate this, let's take the example of a college database where new students are being added. In this example, we have a table called students where we want to insert new student data. The table contains columns for student ID, name, age, and enrollment date.

## Insert a single record

To insert a new student, we write the insert into command followed by the table name students. Next, we add the column names within a pair of parenthesis: ID, name, age, and enrollment date. Then, we use the values keyword and insert the values we want to assign to each column within a pair of parenthesis. For example, if we want to add a new student named John with an ID of 1, age 20, and an enrollment date of 2021/01/15, the statement would look like this:

```sql
INSERT INTO students (ID, name, age, enrollment_date) 
VALUES (1, 'John', 20, '2021/01/15');
```

It is important to use the correct format for dates as specified in the table, otherwise, an error message will appear.

## Insert multiple records

It's also possible to insert multiple records of data into the table at the same time. To do this, we use the same insert into command, followed by the table name, and the column names within a pair of parenthesis. Then, we use the values keyword and insert multiple records of data, separated by a comma.

For example, if we wanted to insert two new students named Mark and Karl, the statement would look like this:

```sql
INSERT INTO students (ID, name, age, enrollment_date)
VALUES
(2, 'Mark', 27, '2020-10-12'),
(3, 'Karl', 26, '2020-10-07');
```

It's important to note that the order in which the columns and values are listed must match up.

 In this example, the first value '2' corresponds to the `ID` column, 'Mark' corresponds to the `name` column, '27' corresponds to the `age` column, and '2020-10-12' corresponds to the `enrollment_date` column.

It's also important to use the correct data types for each value, for example, strings should be enclosed in single or double quotes. When executing this statement, the database will insert two new rows into the students table with the values specified in the statement. It's also worth mentioning that if you don't specify the column names, MySQL will insert the values in the order of the columns in the table.

# Select statement

With the SQL SELECT statement, you can retrieve data from a database table. The basic syntax for the SELECT statement is as follows:

```sql
SELECT column1, column2, ...
FROM table_name;
```

In our example, we want to retrieve all the data from the player table, so we use the wildcard (*) to select all columns in the table. 

The FROM keyword is followed by the table name, in this case, "players".

You can then execute the statement to see the output which is all data available in the player table.

```sql
SELECT * FROM players;
```

# Conclusion

In summary, in this video, we learned how to add new data to tables using the INSERT INTO statement, and how to retrieve existing data from tables using the SELECT statement. By understanding these basic SQL commands, you'll be able to manipulate and manage your databases with ease.