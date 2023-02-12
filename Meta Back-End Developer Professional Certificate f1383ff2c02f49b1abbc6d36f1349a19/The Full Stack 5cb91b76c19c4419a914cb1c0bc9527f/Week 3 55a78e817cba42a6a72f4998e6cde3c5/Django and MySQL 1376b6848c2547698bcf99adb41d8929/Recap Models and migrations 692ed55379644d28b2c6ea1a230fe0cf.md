# Recap: Models and migrations

# Introduction

Models are the M in the Model, View, Template (MVT) architecture used by Django and models are widely considered to be one of the best features of Django.

Object Relational Mapping, or ORM, is the **ability to create a SQL query using an object-oriented programming language such as Python.** This enables quick turnaround time in fast production environments where constant updates are the order of the day.

In this reading, you will learn about the models used in Django and how you can use migrations to perform ORM on these models.

# ****ORM and CRUD operations in models****

![Untitled](Recap%20Models%20and%20migrations%20692ed55379644d28b2c6ea1a230fe0cf/Untitled.png)

Each model is a Python class which in turn is a subclass of **`Django.db.models.Model`**

Each attribute of the model represents a database field. 

Essentially, you can think of a model as a Python object, and models help developers create, read, update and delete objects, commonly called CRUD operations. 

The models that you create are saved in the **`models.py`** file that is inside the Django app. Examine the example below of the SQL syntax and the corresponding Django models for creating a table called **`User`**:

### ****SQL syntax****

```jsx
CREATE TABLE user (
    "id" serial NOT NULL PRIMARY KEY,
    "first_name" varchar(30) NOT NULL,
    "last_name" varchar(30) NOT NULL
);
```

### ****Corresponding Django code****

```jsx
from django.db import models

class User(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
```

The database rows, **`first name`** and **`last name`,** are equivalent to attributes in Django. 

The **`id`** in case of the **`User`** model is auto-generated while performing migrations. Additionally, the functions called on the models object like **`CharField`** are called **`Formfield`**. 

Form fields determine the data type of the attribute.

Let's briefly explore simple examples of models and their associated SQL methods to perform CRUD operations.

### Create

Django:

```jsx
Django
new_user = User(id=1, "John", "Jones")
new_user.save()
```

SQL:

```jsx
INSERT INTO User (id, name, last_name) VALUES (1, "John", "Jones");
```

### Update

Django

```jsx
user = User.objects.get(id=1)
user.last_name = "Smith"
user.save()
```

SQL

```jsx
UPDATE user(id, first_name, last_name)
SET last_name = "Smith"
WHERE id = 1
```

### Delete

Django

```jsx
user = User.objects.get(id=1)
user.delete()
```

SQL

```jsx
DELETE FROM user WHERE id = 1
```

Django ORM provides a large number of options for SQL queries that can be configured and this can be explored on the [official website](https://docs.djangoproject.com/en/4.1/topics/db/queries/).

## raw() function

Django processes data in the form of a QuerySet object and you can also directly use SQL queries on it using the **raw()** function. For example, in the command prompt inside a `**Django project**`, you can enter the Django shell and enter the following code:

```jsx
people = Person.objects.raw('SELECT id, first_name FROM myapp_person')
```

This code accesses the object from the **`Person`** model that was created. The **`raw()`** function then runs a SQL query to select id and first name from the **`myapp_person`** table that was generated.

Building on this example, a query to print the contents of the entry for the selected **id** will be:

```jsx
for p in Person.objects.raw('SELECT id, first_name FROM myapp_person'):
            print(p.first_name, p.last_name)
```

This will print a result in the console such as:

```jsx
**Jesse Rogers**
```

# ****Model relationship****

Model relationships can be of one of the following types:

- One-to-one
- One-to-many
- Many-to-many

If a primary key is in one model, and only one record exists in the other related model, the two models are said to have a one-to-one relationship.

In a one-to-many relationship, one object of a model can be associated with one or more objects of another model. For example, a teacher is qualified to teach a subject, but there can be more than one teacher in a college who teaches the same subject.

In a many-to-many relationship, multiple objects in one model can be associated with multiple objects in another model.

An example of this many-to many relationship is below:

```jsx
class Teacher(models.Model): 
    teacherID = models.IntegerField(primary_key=True) 
    qualification = models.CharField(max_length=50) 
    email = models.EmailField(max_length=50)

class Subject(models.Model): 
    subjectcode = models.IntegerField(primary_key = True) 
    name = models.CharField(max_length=30) 
    credits = model.IntegerField() 
    teacher = model.ManyToManyField(Teacher)
```

These relationships replicate the table relationships in SQL. Relationships are a big concept, but primarily it involves the understanding and use of foreign keys. Foreign keys are represented in Django by the argument called **`Foreign Key`** which is passed inside the **`Formfield`**.

In the following example, a one-to-many relationship can be defined for two models in Django: **Subject** and **Teacher**.

```jsx
class Subject(models.Model): 
    Subjectcode = models.IntegerField(primary_key = True) 
    name = models.CharField(max_length=30) 
    credits = model.IntegerField() 

class Teacher(models.Model): 
    TeacherID = models.ItegerField(primary_key=True) 
    subjectcode=models.ForeignKey( 
                Subject,  
                on_delete=models.CASCADE 
                  ) 
    Qualification = models.CharField(max_length=50) 
    email = models.EmailField(max_length=50)
```

Once you have created a model inside the **`models.py`** file, the next step, **migrations**, is the most important one in Object Relationship Mapping in Django.

# Migrations

Migrations in Django help developers to create and make changes to the models that represent a database schema.

In a relational database, data is organized in tables and models are used to represent these tables stored in the database. Migrations are tied into Django models and stored as migration files in a migrations folder inside each app.

# Migration commands

For example, suppose you want to add a new column called **`City`** to the **`User`** table. 

Without an ORM like the one Django provides, you would have to log into the database and run an SQL **`ALTER`** statement. You can use the **`ALTER`** statement to alter a specific table to add a column of whatever type is required. When the statement runs, the **`User`** table updates with another column called `**City**`.

However, in Django, the **`User`** table is created using a model which is a class-based representation of the **`User`** table in the database. So, instead of writing the SQL query, you only need to add the new attribute to the model. Then you run the migration scripts to implement the changes. Once the migrations scripts run, the changes are applied.

Migration in Django is performed in two steps using specific commands.

To create a migration:

```jsx
python3 manage.py makemigrations
```

To apply the migration:

```jsx
python3 manage.py migrate
```

In addition to applying changes to the models in your project, **migrations also perform syncing and version control for your database schema.** Now that you understand the basics of migrations, you also have to learn about the history of changes or version control that happens when you perform migrations.

# History of changes

To take an example, let's say you are adding an extra attribute to a model or changing an attribute name. There are occasions when multiple users use more than one database and migrations ensure schema changes are applied and updated in the database. 

In Django, a developer must create the change directly in the model, then apply the migration by using the migration scripts.

Another great advantage of using migrations is that it avoids repetition. Once you create a model, writing SQL queries to create corresponding databases for it is repetitive. Migrations generated from the models help prevent such duplication of efforts.

Take note that this history of changes is maintained by Django in migration files. These files are stored in a migrations folder inside the specific app directory of the Django project.

If you run a command such as:

```jsx
show migrations
```

It returns an output such as:

```jsx
[X] 0001_initial
 [X] 0002_logentry_remove
menu_items
 [X] __init__
 [X] 0001_initial
 [X] 0001_alter_menu_items
```

This shows all the migration changes and files generated from those migrations. Django automatically generates the file names in line with the actions performed in the given migrations or the timestamp.

The **`X`** symbol represents the status of applying migrations after it has been made. 

This is after the command **`makemigrations`**, but before the command **`migrate`**. After applying migrations, Django does not apply a new migration to the same database again unless it detects changes.

# Logic behind migrations

Django creates a new table called **`Django migrations`** with reference to the migration files. To summarize the purpose of migration, every time a migration is run: 

- The table is updated with the latest changes
- The table is checked prior to the migration script running
- It ensures that the scripts have run and specifies which ones need to be applied

A typical migration file will look like this:

```jsx
dependencies = [
('LittleLemonDRF', '0001_initial'),
    ]

    operations = [
        migrations.CreateModel(
            name='table_customers',
            fields=[
                ('id', models.BigAutoField(auto_created=True, primary_key=True,   serialize=False, verbose_name='ID')),
                ('first_name', models.CharField(max_length=200)),
            ],
        ),      
    ]
```

It contains mainly **dependencies that refer to the previous migration** that must be applied before this, and operations that refer to actions performed in the given migration.

# Conclusion

While the topics of models, ORM and migrations are pretty broad, this reading gave you a brief overview of the most important aspects of models in Django.