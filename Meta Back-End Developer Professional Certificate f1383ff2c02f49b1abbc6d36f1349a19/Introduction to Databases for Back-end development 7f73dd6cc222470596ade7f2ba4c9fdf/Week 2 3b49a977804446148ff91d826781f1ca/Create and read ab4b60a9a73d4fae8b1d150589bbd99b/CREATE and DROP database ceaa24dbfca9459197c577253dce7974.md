# CREATE and DROP database

Creating and managing a database that can store vast amounts of information, such as the ones used by online bookstores, can seem like a daunting task. However, the answer lies in utilizing SQL (Structured Query Language) create and read commands. These commands allow you to create, alter, and delete databases and their respective tables in an organized and efficient manner.

In this text, you will learn how to use SQL to create a new database and how to drop or delete an existing database. However, before diving into the technical aspects of SQL commands, it's crucial to have a clear understanding of the purpose of the database.

For example, if you're building a database for an online bookstore, you need to consider what types of data will be stored in it, such as book titles, authors, customers and sales. This data needs to be organized and stored in relevant tables within the database, so that users can easily access, retrieve and update the information as needed.

# Creating a database

To create a new database using SQL syntax, you start by typing the keywords "CREATE DATABASE" followed by the name of your new database. For example, to create a new database called bookstore2_db, you would type:

```sql
CREATE DATABASE bookstore2_db;
```

It's important to give your database a meaningful and relevant name that accurately represents the purpose of the database. Additionally, database names must be unique and can only have a maximum of 63 characters. If the name of your database does not meet these requirements, an error message will appear.

# Deleting a database

If you no longer need a specific database, you can drop or delete it using the DROP DATABASE statement in MySQL. This statement is used to delete an existing database and all its objects like tables, indexes, views, etc. The basic syntax of the DROP DATABASE statement is as follows:

```sql
DROP DATABASE database_name;
```

It is important to note that when you drop a database, all the data and objects within the database are permanently deleted and cannot be recovered. Therefore, before dropping a database, it is important to make sure that you have a backup of all the data and objects you need.

Let's take a look at an example of how to drop a database using the bookstore_db2 example we created earlier. First, you need to select the database you want to drop using the USE statement. For example:

```sql
USE bookstore_db2;
```

Then, you can use the DROP DATABASE statement to delete the database, like so:

```sql
DROP DATABASE bookstore_db2;
```

When you run this statement, MySQL will prompt you to confirm that you want to delete the database. If you confirm, the bookstore_db2 database and all its objects will be permanently deleted.

It's important to note that you can only drop a database you have the DROP privilege on. Also, you can't drop a database that is currently in use, you have to remove all connections to it before.

In summary, in this video you learned how to create a new database and delete an existing one using the CREATE DATABASE and DROP DATABASE statements in MySQL. You also learned some of the important considerations to keep in mind when working with these statements, such as the importance of making sure you have a backup of your data before dropping a database.

# Additional

You can use the mysql commands to check the available databases by running

```sql
SHOW DATABASES;
```

and select the database you want to use by running

```sql
USE DATABASE_NAME;
```

It's recommended to also check the privileges you have on a specific database by running

```sql
SHOW GRANTS;
```