# Migrations

# Introduction

In the world of web application development, application requirements constantly change, and it's a developer's job to implement these changes. 

One common task is to alter the data model of the application. 

In Django, **developers use something called migrations to make changes to the models representing the database schema.**

# What are migrations

- **Django is designed to work with a relational database management system** like PostgreSQL, MySQL, or SQLite, and in a relational database, data is organized in tables. By now, you know that you can use **models to represent data tables stored in the database**. The models define the database fields which correspond to the columns in their associated database tables.
- Migrations are how Django records changes made to models and implements these changes to the database schema. They are tied into Django models and stored as migration files in a Migrations folder inside each app. **Migrations are a way of applying changes to the database schema without writing SQL.**

# Examples

Suppose you wanted to add a new column called City to the User table. Without an ORM like the one Django provides, a developer must log in to the database and run a SQL alter statement. 

In Django, the User table is created using a model which you may recall is a class-based representation of the User table in the database. So instead of writing the SQL query, you only need to add the new attribute to the model, then run the migration scripts to implement the changes.

For example, to add a new column called "city" to the "users" table, you would need to add the new attribute 'city' to the User model, then run the migration command.

```python
class User(models.Model):
    first_name = models.CharField(max_length=100)
    last_name = models.CharField(max_length=100)
    city = models.CharField(max_length=100)
```

```python
python manage.py makemigrations
python manage.py migrate
```

You can also use migrations to update a column name or even delete a model. Once the migration scripts run, the changes are applied.

Deletion can also be done using migrations by removing the attribute from the model and then running the migration command

```python
class User(models.Model):
    first_name = models.CharField(max_length=100)
    last_name = models.CharField(max_length=100)
```

```python
python manage.py makemigrations
python manage.py migrate
```

# Conclusion

Django's migrations provide developers with a way of applying changes to the database schema without writing SQL queries. 

Migrations are tied into Django models and stored as migration files in a Migrations folder inside each app. The migration script is a set of instructions on what models to create against the database. 

By using migrations, developers can easily create, update, and delete fields and tables without the need to write SQL. **Additionally, migrations make it easy to track changes to the database schema over time and easily rollback to a previous state if needed.** 

With the use of migrations, the development process becomes more efficient and streamlined, allowing developers to focus on implementing new features instead of worrying about managing the database.