# Working with databases and models

# Introduction

In this video, you will be recapitulating the concepts of working with databases and models in Django. You will recall that Django uses the Model-View-Template (MVT) architecture and the model represents the data layer of the application.

# ****Django ORM****

The Django Object-Relational Mapping (ORM) allows you to interact with the database in an object-oriented manner. The model is at the core of the Django ORM and is the definitive source of information about the data. Each model maps to a single database table.

# Model definition

A model is a Python class that subclasses the **`django.db.models.Model`** class. It has one or more class attributes, which map to columns in the table. The model class maps to a database table.

# [Models.py](http://Models.py) file

You declare one or more model classes in a **`models.py`** file in the app package folder. It is important to remember to add the app to the **`INSTALLED_APPS`** list in the project's **`settings.py`** module.

# Migrations

The Django ORM translates the model definitions into the corresponding tables in the database using a process called migrations. 

You use the command **`python manage.py migrate`**to populate the database with the tables used by the pre-installed applications. 

You generate a migration script to create the table structure for models in the rest of the apps using the command **`python manage.py makemigrations`**. 

The migration scripts are stored in a **`migrations`** sub-package in the app package folder and are incrementally auto-numbered. You run the **`python manage.py migrate`** command to execute the create table queries for building the tables.

# ****Updating Models****

Every time you need to make changes in the structure of the model, such as adding, modifying, or removing a field attribute of a model class, run the **`python manage.py makemigrations`**
 command to propagate the changes to the mapped table. Django's migration mechanism also acts as version control, and you can fall back on the database state at any previous position with the help of a numbered migration script.

# ****Interacting with the model****

You can interact with the model and the table directly from inside the Django Shell. 

To open the Django Shell, run the command **`python3 manage.py shell`**. 

In this interactive shell, you can import the model you have defined. For example, if you have a **`Menu`** model in the **`littlelemon`** app, you use the **`import`** statement to import the model. The model class contains methods to add, update, and delete records.

# ****Django Admin Interface****

You can also access the model from the Django Admin interface. To do this, you must register the model with the admin site.

# Conclusion

In this video, you had a recap of working with databases and models in the Django Framework.