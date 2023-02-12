# Module summary: The full stack using Django

# Recap of Django

- Django is a web framework for Python that enables you to build full-stack web applications.
- Some of its features include:
    - URL routing
    - Object-relational mapping (ORM)
    - Built-in administrative interface

# Recap of APIs

- APIs, or application programming interfaces, allow different software systems to communicate with each other.
- Some of the key elements of an API include:
    - Endpoints
    - Requests and responses
    - HTTP methods (e.g. GET, POST, PUT, DELETE)

# Environment Check

- In order to build a full-stack web application with Django, you need to have certain tools installed.
- You need to install:
    - Django
    - Django Rest Framework (DRF)
    - A virtual environment tool (e.g. pipenv)
    - A MySQL client library (e.g. mysqlclient)
- You should also test your MySQL connection to make sure it's working properly.

# Recap of Databases and MySQL

- Databases are used to store and manage data in a structured way.
- MySQL is a popular open-source relational database management system.
- To install MySQL on a Mac using homebrew, you can use the following command in the terminal:

```jsx
brew install mysql
```

- To connect to MySQL from the command line, you can use the following command:

```jsx
mysql -u [username] -p
```

# Recap of Models and Migrations

- Models are Python classes that represent the structure of data in your application.
- Migrations are a way to update your database tables as your models change over time.
- To create a model in Django, you can define a class that inherits from **`django.db.models.Model`** and add fields to it.
- To create a database table for a model, you can use the following command:
    
    ```jsx
    python manage.py makemigrations
    ```
    
- To apply migrations to your database, you can use the following command:
    
    ```jsx
    python manage.py migrate
    ```
    

# Configuring Django to connect to MySQL

- To configure Django to connect to a MySQL database, you need to update the **`DATABASES`** setting in your settings file.
- The **`DATABASES`** setting should include the following information:
    - Engine (e.g. **`'django.db.backends.mysql'`**)
    - Name (e.g. **`'mydatabase'`**)
    - User (e.g. **`'mydatabaseuser'`**)
    - Password (e.g. **`'mypassword'`**)
    - Host (e.g. **`'localhost'`**)
    - Port (e.g. **`3306`**)

# Forms and ModelForms

- Forms are a way to collect data from users in a web application.
- Django provides a form class that makes it easy to create and process forms.
- ModelForms are a type of form that is based on a model.
- To create a model form, you need to do the following:
    - Create a model
    - Create a model form using the model
    - Configure the view to process form data

# Fetching data using JavaScript

You learned how to use native JavaScript functionalities in forms.

- JavaScript helps with:
    - Processing forms
    - Templating with libraries such as Bootstrap
    - Input validation
    - Form reset