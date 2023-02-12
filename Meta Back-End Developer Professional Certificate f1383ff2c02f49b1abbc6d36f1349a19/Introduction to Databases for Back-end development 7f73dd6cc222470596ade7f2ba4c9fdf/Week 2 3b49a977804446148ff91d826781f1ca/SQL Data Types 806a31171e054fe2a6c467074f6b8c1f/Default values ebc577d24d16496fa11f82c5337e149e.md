# Default values

# Introduction

To ensure the accuracy and reliability of the data in your database, you must limit the type of data they can go into your database table. In this video, you'll learn how to describe the purpose of constraints in a database and identify default constraints to set default values in a table.

# **Understanding Constraints**

Database constraints are used to limit the type of data that can be stored in a table. This ensures that all data inserted into the table is accurate and reliable. If the database dictates a violation between the constraint and the data operations, then it aborts these operations.

An example of a violation might be an attempt to insert or upload invalid data to a table. The database realizes that the data is invalid and rejects it. Constraints can be column level where the rule applies to a specific column. They can also be applied at table level. For example, I could use the foreign key constraints to prevent actions that will destroy links between tables.

# NOT NULL Constraint

- Two of the most used database constraints include NOT NULL, a method of preventing empty value fields, and DEFAULT, a method of assigning default values. For now, let's begin our exploration of default values with a NOT NULL constraint.
- The NOT NULL SQL constraint is used to ensure the data fields are always completed and never left blank.

## Example

Let's explore this concept using the example of a table from an online store that records the IDs and names of customers. The table records this data in the customer ID and customer name columns. These columns must always contain data. If there's no data or values inserted into either of these columns, then the creation of a new customer record is aborted.

The following is an example of how to create a table with a NOT NULL constraint for customer ID and customer name columns in MySQL:

```sql
CREATE TABLE customer
(
  customer_id INT NOT NULL,
  customer_name VARCHAR(50) NOT NULL
);
```

The NOT NULL default value is implemented using a SQL statement. In the example above, I use the **`CREATE TABLE`** clause to define the table name, followed by a pair of parenthesis. Within the parentheses, I added two columns; **`customer_id`** and **`customer_name`**. 

I also defined each column with relevant data types. **`INT`** for **`customer_id`** as it stores numeric values, and **`VARCHAR(50)`** for **`customer_name`** as it stores string values with a maximum length of 50 characters. Finally, I declared a NOT NULL constraint for each column using the **`NOT NULL`** keyword. This makes sure that neither column will accept no values.

Now, any operation that attempts to place a null value in these columns will fail, like inserting or updating data:

```sql
INSERT INTO customer (customer_id, customer_name)
VALUES (NULL, "Jane Doe");
```

The above SQL statement tries to insert a new customer record with a NULL value for the customer ID column, but it will fail because the customer ID column has a NOT NULL constraint.

This will result in an error message similar to:

```sql
Error Code: 1048. Column 'customer_id' cannot be null
```

Alternatively you can include an explicit default value for the fields that have default value, in this case the customer table would look like this:

```sql
CREATE TABLE customer 
(
    customer_id INT NOT NULL AUTO_INCREMENT,
    customer_name VARCHAR(50) NOT NULL,
    PRIMARY KEY (customer_id)
);
```

With this you could insert new customer record without providing an explicit value for the customer_id, as the AUTO_INCREMENT will handle it:

```sql
INSERT INTO customer (customer_name)
VALUES ('Jane Doe');
```

This would insert a new record with customer_id 1, and customer_name 'Jane Doe’.

# DEFAULT Constraint

Next, let's look at how the DEFAULT constraint works in a table. The DEFAULT constraints sets a default value for a column of no value is specified. This means that if no data is entered for a specific field within a column, then the table will automatically insert a default value instead. 

To gain a better understanding of default values, let's look at a table that holds player records for a football club's database:

```sql
CREATE TABLE player 
(
    player_name VARCHAR(255) NOT NULL,
    city VARCHAR(255) DEFAULT 'Barcelona'
);
```

The table is called player table and contains two columns "player_name" and "city", and we want to set the default value for the "city" column to "Barcelona". 

Now, if we were to insert a new player into the table without specifying a value for the "city" column, the default value of "Barcelona" would be inserted automatically.

```sql
INSERT INTO player (player_name)
VALUES ("Lionel Messi");
```

As the city is a not null column and we did not provide the value, so it will insert the default value in the city column which is 'Barcelona’.

You can also update the default value of a column that already exists in a table. 

For example, if we wanted to change the default value for the "city" column to "Madrid" instead of "Barcelona" in the above example:

```sql
ALTER TABLE player
ALTER COLUMN city
SET DEFAULT 'Madrid';
```

It is important to note that the DEFAULT constraint does not affect existing data in a table. It only applies to new data being inserted or uploaded in the future. Also, the default value is not enforced if a value is specified in the insert statement.

You should now be able to explain how the DEFAULT constraint works in a database and how to set default values in a table using SQL. The default constraint is a powerful tool that can help ensure your data remains accurate and reliable.