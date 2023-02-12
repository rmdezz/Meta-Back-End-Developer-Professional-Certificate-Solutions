# Recap: Django setup

# Introduction

As you build a back-end application using Python's Django framework, you will need to have it installed on your machine. You need Python on your local machine to start.

# ****Installing Python****

If you don't already have it, download the appropriate installer for the operating system and your machine's architecture from [https://www.python.org/downloads/](https://www.python.org/downloads/).

# Installing VS Code

It always helps to use an IDE to perform application development efficiently. You will be using VS Code while working on this Capstone project. Download and install VS Code from the official website [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download).

Choose the appropriate installer depending on your operating system and architecture (32 bit or 64 bit).

# ****Setting up the virtual environment****

Python recommends using separate virtual environments for each project to avoid a clash of dependencies of various projects.

The standard method of creating a virtual environment is using the **`venv`** module in Python's standard library.

It's important to remember that a virtual environment has its own copy of the Python interpreter and the library.

```jsx
python –m venv c:\workspace
```

Enter this directory, activate the virtual environment, and start VS Code from inside it.

```jsx
C:\workspace>scripts\activate 
(workspace) C:\workspace>code .
```

Once inside VS Code, choose the Python interpreter of the current virtual environment.

# Installing Django

Open the command terminal, and install the Django framework by entering the following command in the terminal:

```jsx
pip3 install django
```

<aside>
🤔 **Tip:** If you get stuck setting up your environment, revise the reading [Working with virtual environments](https://www.coursera.org/learn/django-web-framework/supplement/rZlSl/working-with-virtual-environments-on-your-local-machine).

</aside>

The installation command will install the Django framework, along with its dependencies.

To check if the installation is correctly installed, enter the following commands:

```jsx
(workspace) C:\workspace>python 
Python 3.10.7 (tags/v3.10.7:6cc6b13, Sep  5 2022, 14:08:36) [MSC v.1933 64 bit (AMD64)] on win32 
Type "help", "copyright", "credits" or "license" for more information. 
>>> import django 
>>> django.__version__ 
'4.1.2'
```

# ****Installing the Django REST Framework and mysqlclient libraries****

Later in the course, you'll also need the **`Django REST Framework`** and **`mysqlclient` libraries**, so you must install them.

# ****Creating a Django project****

You can quickly build a minimal Django project and see if it runs satisfactorily.

Use the **`django-admin`** command line utility to start a new Django project.

```jsx
django-admin startproject littlelemon
```

# ****Launching the development server****

Step into the **`littlelemon`** directory, and use **`manage.py`** script to launch Django's development server.

```jsx
(workspace) C:\workspace>cd littlelemon 
(workspace) C:\workspace\ littlelemon>python manage.py runserver 
Watching for file changes with StatReloader 
Performing system checks... 
System check identified no issues (0 silenced). 
You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions. 
Run 'python manage.py migrate' to apply them. 
November 29, 2022 - 17:13:39 
Django version 4.1.2, using settings 'lemonlittle.settings' 
Starting development server at http://127.0.0.1:8000/ 
Quit the server with CTRL-BREAK. 
[29/Nov/2022 17:13:47] "GET / HTTP/1.1" 200 10681
```

Open a new browser window and paste the localhost URL [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

![Untitled](Recap%20Django%20setup%20629993d0dbfc4bfda5e4f3eea37b4759/Untitled.png)

A congratulations page should load in your browser, meaning Django has been installed successfully.

# ****Summary****

In this Reading, you learned how to install a Django project and launch the development server.