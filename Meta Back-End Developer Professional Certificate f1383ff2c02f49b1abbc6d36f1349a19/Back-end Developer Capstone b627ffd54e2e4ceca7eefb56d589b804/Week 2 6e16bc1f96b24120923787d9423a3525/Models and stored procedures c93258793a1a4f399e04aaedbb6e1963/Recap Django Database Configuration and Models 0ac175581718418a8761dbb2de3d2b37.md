# Recap: Django Database Configuration and Models

# Introduction

Django employs the **`MVT`** architecture, wherein the model represents the application's data layer.

The model is at the core of Django's Object Relation Mapping (**Django ORM**).

It is the single, definitive source of information about your data, where each model maps to a single database table.

A model is a Python class that subclasses the Model class found in the **django.db.models module**.

Generally, the user-defined model has one or more class attributes. Just as the model class maps to a database table, the class attribute is mapped to a column in the table.

Django provides a mechanism to perform CRUD operations using an object-oriented **`QuerySet API`** when the model gets mapped to a table.

This process frees the developer from executing raw SQL queries.

# Database configuration

You can choose from various databases supported by Django. Officially supported databases are: 

- PostgreSQL
- MariaDB
- MySQL
- Oracle
- SQLite

In addition, you can use other types of databases with the help of third-party database back end modules.

The choice of database back end is registered in the Django project's **settings.py** module.

The **`DATABASES`** variable in this module sets the back end to be used, the name of the database, and the credentials for accessing the database if required.

The Django project set up with the **`startproject`** command is configured to use the SQLite database by default. The DATABASES definition in the settings file reads like the following:

**settings.py**

```jsx
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

After you create the project, run the migrate command:

```jsx
python3 manage.py migrate
```

The tables required for the pre-installed apps are created in the database, located in the **BASE_DIR** by default. You can use an SQLite viewer to confirm this:

![Untitled](Recap%20Django%20Database%20Configuration%20and%20Models%200ac175581718418a8761dbb2de3d2b37/Untitled.png)

Django places app-specific models in the **models.py** file in the app package folder.

To create the mapped table in the database, run the commands **makemigrations** and then **migrate**.

# ****Using another database****

To use another type of database instead of the default SQLite, you need to change the **DATABASES** configuration in the **settings.py** file.

Most of the relational database types are server-based. Hence, Django must know the host and port on which the database is running and the user's credentials, such as username and password.

You will also need the **DBAPI-compatible** database driver for your intended database.

# ****Using the MySQL database****

Suppose you intend to use a MySQL database as the back end for your Django application. In that case, you must first install the **mysqlclient** driver with pip.

```jsx
pip3 install mysqlclient
```

Then, replace the **`DATABASES`** configuration with the following block of code:

**settings.py**

```jsx
DATABASES = {  
    'default': {  
        'ENGINE': 'django.db.backends.mysql',  
        'NAME': 'my_database',  
        'USER': 'root',  
        'PASSWORD': 'your_password',  
        'HOST': '127.0.0.1',  
        'PORT': '3306',  
        'OPTIONS': {  
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'"  
        }  
    }  
}
```

# ****Other important configuration settings****

**`CONN_MAX_AGE:**` This parameter defines the maximum lifetime of a connection. The default value is 0, which preserves the historical behavior of closing the database connection at the end of each request.

To enable persistent connections, set `CONN_MAX_AGE` to a positive integer of seconds. For unlimited persistent connections, you can set it to None.

**`AUTOCOMMIT:`** Default: True. Set this to False to disable Django's transaction management and implement your own.

**`OPTIONS:`** Default: {} (Empty dictionary). Extra parameters to use when connecting to the database. Available parameters vary depending on your database backend.

For MySQL, you can specify the connection parameters in the options using the following code:

**settings.py**

```jsx
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'OPTIONS': {
            'read_default_file': '/path/to/my.cnf',
        },
    }
}

# my.cnf
[client]
'NAME': 'my_database'
'USER': 'root'
'PASSWORD': 'your_password'
default-character-set = utf8
```

**SET sql_mode = 'STATIC_TRANS_TABLES'**, which handles invalid or missing values from being stored in the database by **INSERT** and **UPDATE** statements.

# ****Using multiple databases****

You can also configure your Django application to use more than one database. There must be a default database and then set the configuration for the other. For example:

**settings.py**

```jsx
DATABASES = {
    'default': { 
        'ENGINE': 'django.db.backends.sqlite3', 
        'NAME': BASE_DIR / 'db.sqlite3', 
    },
    'mydb': {   
 
        'ENGINE': 'django.db.backends.mysql',   
        'NAME': 'my_database',   
        'USER': 'root',   
        'PASSWORD': 'your_password',   
        'HOST': '127.0.0.1',   
        'PORT': '3306',   
        'OPTIONS': {   
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'"   
        }
```

# ****Conclusion****

In this Reading, you revised configuring a database in Django and how to translate the model structure to the database table.