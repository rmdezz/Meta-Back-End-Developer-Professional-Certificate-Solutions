# SELECT DISTINCT Clause

# Introduction

The SELECT DISTINCT statement is used to retrieve unique values from a table. 

This can be useful when you have a table with duplicate values and you want to retrieve a distinct set of results. In this guide, we will explain what the SELECT DISTINCT statement is, demonstrate how to use it in MySQL, and provide examples of how it interacts with single columns, multiple columns, and null values.

# Basic Syntax

The basic syntax for the SELECT DISTINCT statement is as follows:

```sql
SELECT DISTINCT column_name(s)
FROM table_name;
```

In this example, you would replace "column_name(s)" with the name(s) of the column(s) that you want to retrieve unique values from, and "table_name" with the name of the table you want to retrieve data from.

# Single Column Example

Consider the following **`students`** table:

| id | name | country |
| --- | --- | --- |
| 1 | Alice | USA |
| 2 | Bob | Canada |
| 3 | Charlie | USA |
| 4 | David | Mexico |
| 5 | Eve | USA |

If you want to retrieve a list of all the different countries that the students in this table belong to, you can use the SELECT DISTINCT statement as follows:

```sql
mysql> SELECT DISTINCT country FROM students;
+---------+
| country |
+---------+
| USA     |
| Canada  |
| Mexico  |
+---------+
```

As you can see, the query returns a list of all the unique combinations of countries and faculties in the **`students`** table, without any duplicates.

If there’s a table named invoices with the same BillingCountry repeated in many instances, you can run the following query to identify what they are:

```sql
SELECT BillingCountry  
FROM invoices 
ORDER BY BillingCountry;
```

```sql
+----------------+
| BillingCountry |
+----------------+
| Argentina      |
| Argentina      |
| Argentina      |
| Argentina      |
| Argentina      |
| Argentina      |
| Argentina      |
| Australia      |
| Australia      |
| Australia      |
| Australia      |
| Australia      |
| Australia      |
| Australia      |
| Austria        |
| Austria        |
| Austria        |
| Austria        |
| Austria        |
| Austria        |
| Austria        |
| Belgium        |
| Belgium        |
| Belgium        |
| Belgium        |
+----------------+
(Output limit exceeded, 25 of 412 total rows shown)
```

<aside>
🤔 In the context of the text, an instance refers to a specific occurrence of a value in a table. In this case, the table is named "invoices" and the value being repeated is "BillingCountry". The query being described is being used to identify which countries have the **most instances** in the table. For example, Argentina and Australia have multiple instances in the table. Each time a specific country appears in the BillingCountry column of the invoices table, it is considered an instance of that country. Intuitively, you can think of instances as "counts" or "occurrences" of a specific value in a dataset.

</aside>

When you look at the result, you’ll notice that there are duplicate values in the BillingCountry column. How can you obtain a list of unique billing countries where the invoices have been raised? Let’s change the SELECT statement by adding the DISTINCT keyword and then run it again.

```sql
SELECT DISTINCT BillingCountry  
FROM invoices 
ORDER BY BillingCountry;
```

```sql
+----------------+
| BillingCountry |
+----------------+
| Argentina      |
| Australia      |
| Austria        |
| Belgium        |
| Brazil         |
| Canada         |
| Chile          |
| Czech Republic |
| Denmark        |
| Finland        |
| France         |
| Germany        |
| Hungary        |
| India          |
| Ireland        |
| Italy          |
| Netherlands    |
| Norway         |
| Poland         |
| Portugal       |
| Spain          |
| Sweden         |
| USA            |
| United Kingdom |
+----------------+
```

This time, the duplicate values are gone and only a unique set of billing countries are returned as the result. Where there are repeating values in the BillingCountry column, for example for Argentina, Australia and Austria. The above SELECT DISTINCT query will eliminate those duplicate rows and generate the result as a unique set of values.

# Multiple Column Example

Consider the following **`students`** table:

| id | name | country | faculty |
| --- | --- | --- | --- |
| 1 | Alice | USA | Science |
| 2 | Bob | Canada | Science |
| 3 | Charlie | USA | Engineering |
| 4 | David | Mexico | Science |
| 5 | Eve | USA | Engineering |

If you want to retrieve a list of all the unique combinations of countries and faculties that the students in this table belong to, you can use the SELECT DISTINCT statement as follows:

```sql

mysql> SELECT DISTINCT country, faculty FROM students;
+---------+---------+
| country | faculty |
+---------+---------+
| USA     | Science |
| Canada  | Science |
| Mexico  | Science |
| USA     | Engineering|
+---------+---------+

```

As you can see, the query returns a list of all the unique combinations of countries and faculties in the **`students`** table, without any duplicates.

If you inspect the values in the BillingCountryand BIllingCitycolumns, you’ll notice that the same billing City repeats for a single billing country. You can run the following code to verify this.

```sql
SELECT BillingCountry, BillingCity  
FROM invoices;
```

```sql
+----------------+---------------+
| BillingCountry | BillingCity   |
+----------------+---------------+
| Germany        | Stuttgart     |
| Norway         | Oslo          |
| Belgium        | Brussels      |
| Canada         | Edmonton      |
| USA            | Boston        |
| Germany        | Frankfurt     |
| Germany        | Berlin        |
| France         | Paris         |
| France         | Bordeaux      |
| Ireland        | Dublin        |
| United Kingdom | London        |
| Germany        | Stuttgart     |
| USA            | Mountain View |
| USA            | Redmond       |
| USA            | Cupertino     |
| USA            | Reno          |
| USA            | Madison       |
| Canada         | Halifax       |
| France         | Paris         |
| United Kingdom | Edinburgh     |
| Australia      | Sidney        |
| Chile          | Santiago      |
| India          | Bangalore     |
| Norway         | Oslo          |
| Brazil         | São Paulo     |
+----------------+---------------+
(Output limit exceeded, 25 of 412 total rows shown)
```

So how can you generate list of unique billing cities within the billing countries?

You can run a query that adds the DISTINCT keyword to the SELECT statement.

```sql
SELECT DISTINCT BillingCountry, BillingCity   
FROM invoices 
ORDER BY BillingCountry, BillingCity;
```

```sql
+----------------+---------------------+
| BillingCountry | BillingCity         |
+----------------+---------------------+
| Argentina      | Buenos Aires        |
| Australia      | Sidney              |
| Austria        | Vienne              |
| Belgium        | Brussels            |
| Brazil         | Brasília            |
| Brazil         | Rio de Janeiro      |
| Brazil         | São José dos Campos |
| Brazil         | São Paulo           |
| Canada         | Edmonton            |
| Canada         | Halifax             |
| Canada         | Montréal            |
| Canada         | Ottawa              |
| Canada         | Toronto             |
| Canada         | Vancouver           |
| Canada         | Winnipeg            |
| Canada         | Yellowknife         |
| Chile          | Santiago            |
| Czech Republic | Prague              |
| Denmark        | Copenhagen          |
| Finland        | Helsinki            |
| France         | Bordeaux            |
| France         | Dijon               |
| France         | Lyon                |
| France         | Paris               |
| Germany        | Berlin              |
+----------------+---------------------+
(Output limit exceeded, 25 of 53 total rows shown)
```

**Note: The ORDER BY clause is added here to sort the values for easy reference.**

The result is a unique set of billing cities retrieved for the billing countries. Basically, there are no duplicate values in the  BillingCity column. 

In other words, when you do a DISTINCT of multiple columns, it looks for a combination of unique values in all those columns. In this example, all combinations of BillingCountryand  BillingCity in the result are unique.

# Null Values Example

Consider the following **`students`** table:

| id | name | country | faculty |
| --- | --- | --- | --- |
| 1 | John | USA | Science |
| 2 | Sarah | Australia | Science |
| 3 | Michael | USA | Science |
| 4 | David | Canada | Science |
| 5 | Emily | USA | Arts |
| 6 | Alex | Australia | Arts |
| 7 | Julia | USA |  |

In this example, we have a new student named Julia Smith from the USA. She's not yet been assigned a faculty or school address. As a result, the faculty column within the students table assigned to Julia Smith contain a value of null.

So let's see what happens when we run the following SELECT DISTINCT statement:

```sql
SELECT DISTINCT country, faculty FROM students;
```

The result will be the following table

| country | faculty |
| --- | --- |
| USA | Science |
| Australia | Science |
| Canada | Science |
| USA | Arts |
| Australia | Arts |
| USA | null |

It's important to note that in the SELECT DISTINCT statement the order of the columns matters. If the order is different you will get different results:

```sql
SELECT DISTINCT faculty, country FROM students;
```

This will give you the following table:

| faculty | country |
| --- | --- |
| Science | USA |
| Science | Australia |
| Science | Canada |
| Arts | USA |
| Arts | Australia |
| null | USA |

As you can see, the order of the columns in the SELECT statement affects the resulting output.

Let’s say there are NULL values in a DISTINCT column(s). For example, in the BillingCity column. You can run the same query as before to get the unique billing cities within the billing countries.

```sql
SELECT DISTINCT BillingCountry, BillingCity   
FROM invoices 
ORDER BY BillingCountry, BillingCity;
```

```sql
+----------------+---------------------+
| BillingCountry | BillingCity         |
+----------------+---------------------+
| Argentina      | Buenos Aires        |
| Australia      | Sidney              |
| Austria        | Vienne              |
| Belgium        | Brussels            |
| Brazil         | Brasília            |
| Brazil         | Rio de Janeiro      |
| Brazil         | São José dos Campos |
| Brazil         | São Paulo           |
| Canada         | Edmonton            |
| Canada         | Halifax             |
| Canada         | Montréal            |
| Canada         | Ottawa              |
| Canada         | Toronto             |
| Canada         | Vancouver           |
| Canada         | Winnipeg            |
| Canada         | Yellowknife         |
| Chile          | Santiago            |
| Czech Republic | Prague              |
| Denmark        | Copenhagen          |
| Finland        | Helsinki            |
| France         | Bordeaux            |
| France         | Dijon               |
| France         | Lyon                |
| France         | Paris               |
| Germany        | Berlin              |
+----------------+---------------------+
(Output limit exceeded, 25 of 53 total rows shown)
```

Provided that for some records the BillingCity column has NULL values, you’ll receive records with a combination of some value for BillingCountry and NULL for BillingCity.

So, it's important to know that SELECT DISTINCT treats any NULL values in the DISTINCT column(s) as unique. Therefore, in this case, it looks for a combination of unique BillingCountry and BillingCity values. Any NULL values in the BillingCity column are considered unique values. For example, **Argentina – NULL** could be one unique combination and **Australia – NULL** could be another.

# ****Using DISTINCT with SQL aggregate functions****

DISTINCT can also be used with SQL aggregate functions like COUNT, AVG, MAX and so on. In this case, you must specify an expression that’s written using some aggregate function. Therefore, it’s not only column names that you can use DISTINCT with but also with expressions.

What if you want to find out the number of unique countries of the customers in the customer table? Run a SELECT statement that uses the aggregate function COUNT on the country column along with DISTINCT.

## Example

```sql
SELECT COUNT(DISTINCT country)  
FROM customers;
```

```sql
+-------------------------+
| COUNT(DISTINCT country) |
+-------------------------+
|                      24 |
+-------------------------+
```

The result that you get is the number of unique countries that the customers come from. Using DISTINCT on the country column/field gives a unique list of countries and the COUNT aggregate function counts the number of results.

# Conclusion

In conclusion, the SELECT DISTINCT statement is useful when you want to retrieve unique values from one or multiple columns in a table. It eliminates any duplicate rows that include the same values in the specified columns, and allows you to retrieve a distinct set of results. 

Here are some important points to remember in terms of SELECT DISTINCT:

- When only one column or expression is provided in the DISTINCT clause, the query will return the unique values for that column.
- When more than one column or expression is provided in the DISTINCT clause, the query will retrieve unique combinations for those columns.
- The DISTINCT clause doesn't ignore NULL values in DISTINCT column(s). NULL values are considered as unique values by DISTINCT.