# Configuring Django to connect to MySQL

MySQL is a popular and widely used database engine that can be used for small and large-scale web applications. In this guide, you'll learn how to use MySQL as the back-end database engine for your Django project.

# Prerequisites

- Terminal access to your Django project directory
- Virtual environment (recommended)
- MySQL client package

# ****Installing the MySQL Client Package****

If you're using pipenv, activate the virtual environment and install the MySQL client package using the following command:

```jsx
pipenv install mysqlclient
```

If you're not using pipenv, use pip or pip3 to install the package:

```jsx
pip install mysqlclient
```

or

```jsx
pip3 install mysqlclient
```

# ****Connecting to the MySQL Server****

Use the following command to connect to the MySQL server from the terminal:

```jsx
mysql -u root -p
```

If MySQL is running on a different port number (e.g., 3307), specify it as well:

```jsx
mysql -u root -P 3307 -p 
```

By default, the host name for MySQL is localhost. If it is different in your computer or server, specify it with the **`-h`** switch:

```jsx
mysql -u root -h 127.0.0.1 -p
```

# Creating a database

In the MySQL Shell, create a database using the following command:

```jsx
create database little_lemon;
```

Check if the database was created successfully by using the following command:

```jsx
show databases;
```

![Screenshot 2023-02-07 at 10.06.32 PM.png](Configuring%20Django%20to%20connect%20to%20MySQL%207562d2e5a5d043f29e754677ea504350/Screenshot_2023-02-07_at_10.06.32_PM.png)

# Configuring Django to use MySQL

In the **`settings.py`** file, change the **`DATABASES`** section to use the MySQL database instead of SQLite:

```jsx
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'little_lemon',
        'USER': 'root',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

# Verifying the connection

Return to the terminal and navigate to your project directory. Run the following commands to make and run migrations:

```jsx
python manage.py makemigrations
python manage.py migrate
```

# ****Checking the Tables in MySQL****

Connect to the MySQL Shell and select the database you created previously:

```jsx
use little_lemon;
```

List the tables created by migrations using the following command:

```jsx
show tables;
```

![Screenshot 2023-02-07 at 10.10.31 PM.png](Configuring%20Django%20to%20connect%20to%20MySQL%207562d2e5a5d043f29e754677ea504350/Screenshot_2023-02-07_at_10.10.31_PM.png)

# Conclusion

You have successfully connected your Django project to MySQL. You learned how to use the MySQL Shell and change the settings in the **`settings.py`** file to make a successful connection, even if your MySQL setup runs with a different host name and port number.