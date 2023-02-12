# ALTER Table Statement

As a database developer, you'll often need to change the structure of a table to keep up with changing requirements. You can use SQL syntax to do this using the ALTER TABLE statement. The basic syntax of this statement is as follows:

```sql
ALTER TABLE table_name
{ADD column_name data_type} | {DROP COLUMN column_name} | {MODIFY COLUMN column_name data_type}
```

In this statement, "table_name" is the name of the table you want to modify, and the curly braces indicate that you can choose to ADD, DROP or MODIFY a column.

For example, let's say you have a students table in a database called college, and you want to add three new columns to the table: age, nationality and country. To do this, you would use the ADD keyword, followed by the name of each column and the data type it should hold, like so:

```sql
ALTER TABLE students
ADD age int,
ADD nationality varchar(255),
ADD country varchar(52);
```

Now let's say you have decided to remove the nationality column, you can use the DROP COLUMN keyword.

```sql
DROP COLUMN nationality;
```

You can also use the MODIFY keyword to change the properties of an existing column. For example, let's say you want to increase the size of the country column from 50 characters to 100 characters, you can use the following query:

```sql
ALTER TABLE students
MODIFY COLUMN country VARCHAR(100);
```

In this way you can use the alter statement to make changes to tables in your database, whether you want to add or delete columns, or change the properties of an existing column. Remember that you must be sure that you know the structure of the table to avoid unwanted consequences like losing data.