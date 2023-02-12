# Exercise: Setting up the Django project

# ****Overview****

In this Capstone project course, you are going to build REST APIs using Django and Django REST Framework.

In this exercise, you will build a Django project for the Little Lemon restaurant.

# Scenario

The owners of the Little Lemon restaurant have hired you to build two APIs. One API to order food using the **Menu API**. You need to build the **Table booking API** to facilitate reserving a table for dining in the restaurant on a specific date and for a certain number of people.

# Steps

## **Step 1**

If your computer doesn’t already have Python installed on it, download and install from the link: [https://www.python.org/downloads/](https://www.python.org/downloads/).

Tip: Make sure to choose the installer for your OS and architecture.

h

## Step 2

You will use VS Code for developing this Capstone project. If not already available locally, install from the link:  [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download).

## Step 3

Create a Python virtual environment, activate it and install Django in it.

```jsx
python –m venv workspace
cd workspace
scripts\activate
scripts\pip3 install django
```

**Note:** The **macOS** commands to activate virtual environment and install Django

```jsx
pip install virtualenv
virtualenvmyenv --python=python3
source myenv/bin/activate
pip install django
```

## Step 4

Open VS code from the workspace directory

```jsx
code .
```

## **Step 5**

From VS Code extension marketplace, install the **Python** extension.

![Untitled](Exercise%20Setting%20up%20the%20Django%20project%20ade43ebfe028401f903f472e3e21bdb2/Untitled.png)

## Step 6

Press **ctrl+shift+p** and select Python interpreter. Choose the interpreter in the virtual environment path.

## Step 7

Open a new **`CMD`** terminal in VS Code. Use the **`startproject`** command of **`django-admin`** utility.

```jsx
django-admin startproject littlelemon
```

**Note:** If the Powershell terminal opens by default, choose **Command Prompt** from the drop down

![Untitled](Exercise%20Setting%20up%20the%20Django%20project%20ade43ebfe028401f903f472e3e21bdb2/Untitled%201.png)

## Step 8

Change the current directory to **littlelemon** and create a **djangoapp** with the name **restaurant**.

```jsx
python manage.py startapp restaurant
```

## Step 9

Open the **`settings.py`** file from the **`littlelemon`** project package in a new VS Code window. Add the restaurant app to the **`INSTALLED_APPS`** list.

## Step 10

From the terminal, start the Django development server with following command:

```jsx
python manage.py runserver
```

**Tip:** It’s safe to ignore the migration related warnings for now.

## Step 11

Open the browser window and enter [http://localhost:8000/](http://localhost:8000/) URL. You should get the page showing the successful installation of Django project.

![Untitled](Exercise%20Setting%20up%20the%20Django%20project%20ade43ebfe028401f903f472e3e21bdb2/Untitled%202.png)

# Conclusion

You have installed Django framework on your computer, and successfully created a Django project.