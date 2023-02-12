# Project structure

When installing Django globally or in a virtual environment, Python recommends using isolated environment libraries and other dependencies required for a particular application.

Python's standard library contains the **`venv`** module which installs a command-line utility called Django-admin in the system path and is located in the scripts folder of your current Python environment.

# Django-Admin

As the name suggests, you use the **`django-admin`** utility to perform various administrative tasks.

- These tasks include:
    - Creating the project and app
    - Performing migrations to generate database tables, whose structure matches data models
    - Running a development server

# What is a project?

A Django project is a Python package containing the database configuration used by various sub-modules (Django calls them apps) and other Django-specific settings.

- To create a new project, you can use the startproject command of Django-admin as follows:
    - The startproject is Django’s default project template
    - It creates the following file structure in the Python environment:
    - If you start VS Code in this folder, the file structure appears in its explorer
        - Folder named demoproject is created in the Python environment folder.
            - contains a script manage.py and another folder of the same name.
1. Check your python version: **`python --version`** command is used to check the version of python3 that is currently installed on the system

```python
python3 --version
```

![Screenshot 2023-01-23 at 1.15.21 PM.png](Project%20structure%20a11ecc7222444dcaabd4ceacc9d2da6f/Screenshot_2023-01-23_at_1.15.21_PM.png)

1. Create a new virtual environment: **`python3 -m venv env`** command is used to create a new virtual environment and naming it 'env'

```python
python3 -m venv env
```

1. Activate the virtual environment: **`source env/bin/activate`** command is used to activate the virtual environment, the command prompt changes to **`(env)`**

```python
source env/bin/activate
```

1. Install the django package in the virtual environment: **`python3 -m pip install django`** command is used to install the django package in the virtual environment created in the previous step

```python
python3 -m pip install django
```

![Screenshot 2023-01-23 at 1.24.10 PM.png](Project%20structure%20a11ecc7222444dcaabd4ceacc9d2da6f/Screenshot_2023-01-23_at_1.24.10_PM.png)

1. Create a new Django project: **`django-admin startproject myProject`** command is used to create a new Django project, named myProject in the current directory

```python
django-admin startproject myProject
```

1. Navigate into the myProject directory:

```python
cd myProject
```

# manage.py

The manage.py script inside the outer demoproject has the same role as the django-admin utility. 

- You can use it to perform various administrative tasks
- In that sense, it is a local copy of the django-admin utility.
- The general usage of [manage.py](http://manage.py/) is as follows:
    - python3 [manage.py](http://manage.py) <command>

Let's explore some of the required command options:

## startapp

As mentioned above, a Django project folder can contain one or more apps. An app is also represented by a folder of a specific file system. The command to create an app is:

```python
python3 manage.py startapp <name of app>
```

You will explore the structure of an app later. 

## makemigrations

Django manages the database operations with the ORM technique. Migration refers to generating a database table whose structure matches the data model declared in the app.

The following command should be run whenever a new model is declared.

```python
python3 manage.py makemigrations
```

## migrate

This command option of manage.py synchronizes the database state with the currently declared models and migrations. 

```python
python3 manage.py migrate
```

![Untitled](Project%20structure%20a11ecc7222444dcaabd4ceacc9d2da6f/Untitled.png)

## runserver

This command starts Django’s built-in development server on the local machine with IP address 127.0.0.1 and port 8000.

```python
python3 manage.py runserver
```

It helps if you don't use this development server in the production environment. 

## shell

This command opens up an interactive Python shell inside the project. This is useful when you are required to perform some quick interactive operations. 

```python
python manage.py shell
```

![Untitled](Project%20structure%20a11ecc7222444dcaabd4ceacc9d2da6f/Untitled%201.png)

Django prefers **IPython** if it is installed over the standard Python shell.

# Project package

The startproject command option of the Django-admin utility creates the folder of the given name, inside which there is another folder of the same name. For example, the command:

```python
django-admin startproject demoproject
```

This creates a demoproject folder, inside which there’s another demoproject folder.

**The inner folder is a Python package.** For a folder to be recognized by Python as a package, it must have a file **__init__.py**. In addition, the **startproject** template places four more files in the package folder:

## settings.py

Django configures specific parameters with their default values and puts them in this file.

The django-admin utility and **`manage.py`** script use these settings while performing various administrative tasks.

## urls.py

This script contains a list of object **`urlpatterns`**. Every time the client browser requests a URL, the Django server looks to match its pattern and routes the application to the mapped view.

The default structure of urls.py contains a view mapped to the project’s Admin site.

```python
from django.contrib import admin 
from django.urls import path 

 urlpatterns = [ 
    path('admin/', admin.site.urls), 
]
```

## asgi.py

This file is used by the application servers following the ASGI standard to serve asynchronous web applications.

## **wsgi.py**

Many web application servers implement the WSGI standard. This script is the entry point for such WSGI-compatible servers to serve your classical web application.

# ****settings.py****

This file defines the attributes that influence the function of a Django application. The **`startproject**` template assigns some default values to these attributes. They may be modified as per requirement during the use of the application.

Let us explain some critical settings.

## **INSTALLED_APPS**

This is a list of strings. Each string represents the path of an app inside the parent project folder. The **`startproject`** template installs some apps by default. They appear in the **INSTALLED_APPS** list.

```python
INSTALLED_APPS = [ 
    'django.contrib.admin', 
    'django.contrib.auth', 
    'django.contrib.contenttypes', 
    'django.contrib.sessions', 
    'django.contrib.messages', 
    'django.contrib.staticfiles', 
]
```

This list must be updated by adding its name whenever a new app is installed.

For example, if we create a **`demoapp`** with the following command:

```python
python manage.py startapp demoapp
```

Then, add the '**demoapp**' string inside the **INSTALLED_APP** list.

```python
INSTALLED_APPS = [ 
    'django.contrib.admin', 
    'django.contrib.auth', 
    'django.contrib.contenttypes', 
    'django.contrib.sessions', 
    'django.contrib.messages', 
    'django.contrib.staticfiles', 
		'demoapp',
]
```

## Databases

This attribute is a dictionary that specifies the configuration of one or more databases to be used by the current Django application. By default, Django uses the SQLite database. Hence, this setting has a pre-defined configuration for it.

```python
DATABASES = { 
    'default': { 
        'ENGINE': 'django.db.backends.sqlite3', 
        'NAME': BASE_DIR / 'db.sqlite3', 
    } 
}
```

The default name of the SQLite database is db.sqlite3, which is created in the parent project folder.

In place of SQLite, you may choose to use any other. For example, for MySQL, the database settings could be as follows:

```python
DATABASES = {   
    'default': {   
        'ENGINE': 'django.db.backends.mysql',   
        'NAME': 'djangotest',   
        'USER': 'root',   
        'PASSWORD': 'password',   
        'HOST': '127.0.0.1',   
        'PORT': '3306',            
    }   
}
```

Note here the default port number for MySQL is **`3306`** as against the default port number **`8000`** used with SQLite in Django.

## **DEBUG = True**

By default, the development server runs in debug mode. This helps develop the application as the server picks up changes in the code and the output can be refreshed without restarting. However, it must be disabled in the production environment.

## ALLOWED HOSTS

This attribute is a list of strings. By default, it is empty. Each string represents the fully qualified host/domain where this Django site can be served. For example, to make the site running on localhost externally visible, you may add 0.0.0.0:8000 to this list.

## ROOT_URLCONF

This setting is a string pointing toward the urls.py module in which the project’s URL patterns are found. In this case, it would be:

```python
ROOT_URLCONF = 'demoproject.urls'
```

## **STATIC_URL**

This setting points to the folder where the static files, such as JavaScript code, CSS files and images, are placed. Usually, it is set to '**static/**' corresponding to the folder of this name in the parent project folder.

# ****Test the installation****

After creating the project, to verify that it is built correctly, start the development server with the following command while remaining in the project’s parent folder:

```python
python manage.py runserver
```

![Screenshot 2023-01-23 at 2.30.59 PM.png](Project%20structure%20a11ecc7222444dcaabd4ceacc9d2da6f/Screenshot_2023-01-23_at_2.30.59_PM.png)

![Screenshot 2023-01-23 at 2.31.16 PM.png](Project%20structure%20a11ecc7222444dcaabd4ceacc9d2da6f/Screenshot_2023-01-23_at_2.31.16_PM.png)

The server starts running at port 8000 of the localhost with IP address 127.0.0.1. Open the browser and enter [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

![Untitled](Project%20structure%20a11ecc7222444dcaabd4ceacc9d2da6f/Untitled%202.png)

If you get this output, the project has been created successfully.

In this reading, you learned how to create a Django project. The file structure of the project has also been explained here. In the end, the installation of the project has been successfully verified.