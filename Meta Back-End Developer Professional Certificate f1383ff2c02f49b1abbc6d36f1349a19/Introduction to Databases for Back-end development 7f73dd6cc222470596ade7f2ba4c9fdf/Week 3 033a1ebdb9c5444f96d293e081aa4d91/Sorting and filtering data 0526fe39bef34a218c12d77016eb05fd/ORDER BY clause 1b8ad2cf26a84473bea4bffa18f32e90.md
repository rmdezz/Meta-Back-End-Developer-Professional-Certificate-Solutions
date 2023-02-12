# ORDER BY clause

The MySQL Database Management System (DBMS) provides several clauses to sort and filter data in a table. One of the most widely used of these is the ORDER BY clause. It allows you to reorder the data in a table by one or more columns. In a table that holds data on students in a college, you could sort the data by date of birth, and the table would then present all students in the order of oldest to youngest.

# Purpose

The ORDER BY clause is an optional clause that can be added to a SELECT statement. Its main purpose is to sort data in either ascending or descending order. For example, you can sort a list of student names in an alphabetical order from A to Z or vice versa.

# Syntax of the ORDER BY Clause

The basic syntax of the ORDER BY clause starts with a SELECT statement, followed by a list of columns to be sorted, separated by commas. Then comes the FROM keyword, followed by the name of the table to be sorted. Finally, the ORDER BY clause is added, followed by the name of the column to be sorted. You can specify the sorting order by appending either ASC for ascending or DESC for descending at the end of the column name.

You can also sort data by multiple columns by listing all columns after the ORDER BY clause and separating them with a comma. Additionally, you can specify all columns after the SELECT keyword by using an asterisk (*).

It's also important to note that the type of data in your table affects how it is ordered. If the column has a numeric data type, the records will be sorted in ascending or descending numerical order, and if a column has a text-based or string data type, then it will be sorted in ascending or descending alphabetical order.

# Examples

## Ordering data by single column

```sql
SELECT ID, first_name, last_name, nationality
FROM student_table
ORDER BY nationality ASC
```

## Ordering data by multiple columns

```sql
SELECT ID, first_name, last_name, nationality, date_of_birth
FROM student_table
ORDER BY nationality ASC, date_of_birth DESC
```

## Ordering data by all columns

```sql
SELECT *
FROM student_table
ORDER BY ID ASC
```

# Conclusion

In conclusion, the ORDER BY clause is a powerful tool that helps you sort data in a table. By mastering its syntax and usage, you can easily sort data in a variety of ways and make it more organized and readable. With the knowledge and examples provided in this text, you will be able to demonstrate the purpose of the ORDER BY clause for sorting data, explain the different forms in which the ORDER BY clause can be used to sort data, and describe how the ascending and descending keywords behave when used in sort columns.