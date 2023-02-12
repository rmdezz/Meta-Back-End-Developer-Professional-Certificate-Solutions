# Setting up a MySQL connection

Django supports a range of databases including MySQL, which is popular for its reliability, scalability, and security. To connect a Django project to a MySQL database, you need to perform the following steps:

# Install MySQL

You can use a package manager such as Homebrew for macOS.

```python
brew install mysql
```

# Install the MySQL client library

This will allow the MySQL database to interact with the Django ORM.

```python
pip3 install mysqlclient
```

# Create a database in MySQL

You can do this by running the following commands in the MySQL shell:

```python
mysql> create database feedback;
mysql> create user 'admindjango' identified by 'password';
mysql> grant all privileges on feedback.* to 'admindjango';
mysql> flush privileges;
```

# Update the settings.py

Update the settings.py file in the Django project to reflect the MySQL connection information.

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'feedback',
        'USER': 'admindjango',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

# Run migrations

Run migrations to apply the changes to the database.

```python
python3 manage.py makemigrations
python3 manage.py migrate
```

With these steps, your Django project is now connected to a MySQL database.