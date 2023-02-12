# Exercise: Connect Django to MySQL

# Lab Assets

You are provided with a basic setup for Django environment for the project and app inside a Zip file below.

[OF-xNIe8S3qh4WcBUXCpug_09bfaab7dc394464b81f691e89b5bdf1_Connect-Django-to-MySQL.zip](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/OF-xNIe8S3qh4WcBUXCpug_09bfaab7dc394464b81f691e89b5bdf1_Connect-Django-to-MySQL.zip)

Note that the virtual environment using **pipenv** has been added as a part of the zip file. You have to activate the virtual environment and ensure the dependencies are installed.

Your goal is to create and connect to a MySQL database that can be used inside a Django project.

# Objectives

- Create new MySQL database credentials
- Update the project settings in Django to enable connection with MySQL

# Introduction

So far, you've learned how to work with the default SQLite database inside your Django project.

In this lab, you will create and connect to an external MySQL database that can be used inside a Django project.

# Initial lab instructions

This lab will require you to modify the **`settings.py`** file.

![Untitled](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Untitled.png)

Additionally, you are required to use the command line console inside the VS Code terminal.

If not open already, go to **`Terminal`** on the Menu bar at the top of your screen and select **`New Terminal**.`

![Untitled](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Untitled%201.png)

You have already built the project named **`myproject`** and added an app inside the project called **`myapp`**.

Follow the instructions below and ensure you check the output at every step.

# Steps

<aside>
🤔 **Note:** *Make sure you have installed MySQL on your local machine and set up the admin user. In this lab, to keep it simple, you are going to begin with the **root** user with credentials as below.*

</aside>

Username: root

Password:

<aside>
🤔 **Note:** *You must know the password set for root. In case you don’t recall, the default password for root if not configured is* **<blank>** *or empty.*****

</aside>

## Step 1

First go to the command line or terminal on your local machine and log into the mysql shell by typing the command:

```jsx
mysql -u root -p
```

Press **`Enter`** and enter the password when prompted.

<aside>
🤔 **Note:** *Depending on the local machine, in some cases you may have to provide admin privileges for this command. This can be done by adding the keyword sudo before the command. For example:* **sudo mysql -u root -p**

</aside>

![Screenshot 2023-02-07 at 10.22.08 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.22.08_PM.png)

## Step 2

Now create a database with the name **menu_db** with the command below:

```jsx
CREATE DATABASE menu_db;
```

<aside>
🤔 **Note:** *The commands in MySQL should end with a semi-colon* *(***;***).*

</aside>

You will receive a confirmation such as the one below:

![Untitled](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Untitled%202.png)

## Step 3

Next, you need to verify that the database is created by typing the command:

```jsx
SHOW DATABASES;
```

![Untitled](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Untitled%203.png)

The output will depend on the databases present on your local machine. Confirm that it includes **`menu_db`** which is the database you have created.

## Step 4

Now open VSCode and In the terminal, run the command that will enable access to mysql and enter the mysql shell by passing the **-u** and **-p** flags that will enable the MySQL console to prompt for a password.

![Screenshot 2023-02-07 at 10.22.49 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.22.49_PM.png)

![Untitled](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Untitled%204.png)

<aside>
🤔 **Note:** *The default password set for mysql here will be* **root***.*

</aside>

## Step 5

Once inside the mysql file, add the command to show the databases already present.

Confirm that the same databases appear in the terminal in VS Code.

![Screenshot 2023-02-07 at 10.23.31 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.23.31_PM.png)

## Step 6

Create a new database with the name **`menu_items`** by running a MySQL query.

![Screenshot 2023-02-07 at 10.23.51 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.23.51_PM.png)

## Step 7

Run the show database command and ensure the **`menu_items`** database gets updated in the list of databases.

![Screenshot 2023-02-07 at 10.24.09 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.24.09_PM.png)

## Step 8

If you want to use a new MySQL user, then create a new user for the database by running the following command:

```jsx
CREATE USER 'admindjango'@'localhost' IDENTIFIED BY 'employee@123!' ;
```

Or simply use the default **`root`** user and its password.

![Screenshot 2023-02-07 at 10.24.51 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.24.51_PM.png)

## Step 9

Run the following command to grant all permissions to the user you have created:

```jsx
GRANT ALL ON *.* TO 'admindjango'@'localhost';
```

![Screenshot 2023-02-07 at 10.25.12 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.25.12_PM.png)

## Step 10

Run the command to flush all the privileges.

<aside>
🤔 **Note:** ***mysqlclient*** *is already installed as the MySQL database connector using **pipenv**.*

</aside>

```jsx
flush privileges;
```

This command reloads the grant tables in the mysql database, which store the privileges that determine the permissions of each user. After making changes to the privileges, **it's a good practice to flush the privileges to ensure that the changes take effect immediately.**

![Screenshot 2023-02-07 at 10.26.27 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.26.27_PM.png)

## Step 11

Run the command to exit the mysql shell.

```jsx
exit
```

![Screenshot 2023-02-07 at 10.26.44 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.26.44_PM.png)

## Step 12

Inside your Django project, open the **`settings.py`** file and go to **`DATABASES`**.

![Screenshot 2023-02-07 at 10.27.13 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.27.13_PM.png)

## Step 13

Select the values assigned to it by default and replace them with the following code:

Replace DB_name, DB_user and DB_password with actual values.

![Untitled](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Untitled%205.png)

```jsx
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'menu_db',
        'HOST': '127.0.0.1',
        'PORT': '3306',
        'USER': 'root',
        'PASSWORD': '66xbo1E#y97L'
    }
}
```

Next, find the configuration for **`INSTALLED_APPS`** and update the value with the name of your app such as:

![Untitled](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Untitled%206.png)

```jsx
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',
]
```

Save the **settings.py** file.

## Step 15

Open the terminal in VS Code and make sure you are inside the folder containing the file **manage.py** and outside the mysql shell prompt.

## Step 16

Run both commands to perform the migration.

```jsx
python3 manage.py makemigrations
python3 manage.py migrate
```

![Screenshot 2023-02-07 at 10.30.35 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.30.35_PM.png)

```jsx
pipenv install myqslclient
pipenv shell
python3 manage.py makemigrations
python3 manage.py migrate
```

![Screenshot 2023-02-07 at 10.32.42 PM.png](Exercise%20Connect%20Django%20to%20MySQL%20fe8fd55683474dfa98e9d2a668651b1d/Screenshot_2023-02-07_at_10.32.42_PM.png)

# Conclusion

In this lab, you practiced connecting your Django application to a MySQL database.