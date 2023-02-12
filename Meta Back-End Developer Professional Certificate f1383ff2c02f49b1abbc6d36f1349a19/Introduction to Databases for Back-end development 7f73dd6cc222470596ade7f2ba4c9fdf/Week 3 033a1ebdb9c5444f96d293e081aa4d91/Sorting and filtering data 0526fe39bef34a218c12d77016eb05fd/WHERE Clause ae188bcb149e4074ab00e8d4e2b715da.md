# WHERE Clause

# Introduction

In this task, we will explore the use of the WHERE clause in SQL to filter data in a MySQL database. We will examine the syntax and usage of the WHERE clause, learn how to filter data using different operators and review examples of its application in various practical scenarios.

# The WHERE Clause

The WHERE clause is used to filter data in a database by specifying a condition. It is particularly useful in retrieving only the records that meet a certain criteria from a table. 

To understand how the WHERE clause works, it may help to break down its syntax in a SQL SELECT statement. 

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
```

- The syntax starts with the standard SQL SELECT statement followed by the columns you want to query.
- Next is the FROM clause followed by the table_name.
- Then you can bring in the WHERE clause, after the WHERE clause, you can specify the condition. This condition serves as filter criteria and only the records that meet the condition will be retrieved.

# Operators in the WHERE Clause

There are a wide range of operators that can be used in the WHERE clause to filter data. Some examples include:

- Equals (=)
- Less than (<)
- Greater than (>)
- Less than or equal to (<=)
- Greater than or equal to (>=)
- Not equal to (!=)
- BETWEEN
- LIKE
- IN

The operator used depends on the type of data you are working with and the specific filter criteria you want to apply. Text values must be enclosed in single quotes when used in the WHERE clause.

# Examples

## Filtering by a single column:

1. To filter the data in the student table for students in the engineering faculty, you would use the following query:

```sql
SELECT * 
FROM student_table
WHERE faculty = 'engineering';
```

## Using the BETWEEN operator:

To filter data in the employee table for employees with salary between $50,000 and $60,000, you would use the following query:

```sql
SELECT * 
FROM employee_table
WHERE salary BETWEEN 50000 AND 60000;
```

## Less Than (<)

To filter data in the sales table for orders with an amount less than $1000, you would use the following query:

```sql
SELECT * 
FROM sales
WHERE amount < 1000;
```

## Greater than (>)

To filter data in the products table for products with a quantity greater than 100, you would use the following query:

```sql
SELECT * 
FROM products
WHERE quantity > 100;
```

## Less than or equal to (<=)

To filter data in the employees table for employees with a salary less than or equal to $75,000, you would use the following query:

```sql
SELECT * 
FROM employees
WHERE salary <= 75000;
```

## Greater than or equal to (>=)

To filter data in the customers table for customers who have made purchases greater than or equal to $500, you would use the following query:

```sql
SELECT * 
FROM customers
WHERE total_purchases >= 500;
```

## Not equal to (!=)

1. To filter data in the inventory table for products that are not out of stock, you would use the following query:

```sql
SELECT * 
FROM inventory
WHERE stock_status != 'out of stock';
```

## LIKE

To filter data in the faculty table for faculty members whose last name starts with "Sm", you would use the following query:

```sql
SELECT *
FROM faculty
WHERE last_name LIKE 'Sm%';
```

In this case, the WHERE clause searches the "last_name" column for values that start with "Sm" followed by any number of characters. The percent sign is used as a wildcard character to represent any number of characters in the pattern.

## IN

To filter data in the students table for students whose major is either Computer Science or Electrical Engineering, you would use the following query:

```sql
SELECT * 
FROM students
WHERE major IN ('Computer Science', 'Electrical Engineering');
```

In this case, the WHERE clause searches the "major" column for values that match either Computer Science or Electrical Engineering.

## Using like and with the underscore (_) operator.

To filter data in the faculty table for faculty members whose last name starts with "S" and has two or more letters after it.

```sql
SELECT *
FROM faculty
WHERE last_name LIKE 'S_%';
```

# Conclusion

The WHERE clause is a powerful tool for filtering data in a MySQL database. By mastering its syntax and usage, you can easily retrieve the specific records you need and make use of different operators to apply filter criteria. With the knowledge and examples provided in this task, you will be able to use the WHERE clause in various practical scenarios and make effective use of the different operators for filtering data.