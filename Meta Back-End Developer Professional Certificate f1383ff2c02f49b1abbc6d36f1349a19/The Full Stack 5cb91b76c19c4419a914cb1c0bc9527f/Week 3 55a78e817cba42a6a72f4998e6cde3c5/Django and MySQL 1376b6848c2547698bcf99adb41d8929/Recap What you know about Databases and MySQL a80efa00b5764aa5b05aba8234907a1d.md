# Recap: What you know about Databases and MySQL

# Introduction to Databases in Django

Databases play a crucial role in web applications and are used for performing operations like create, read, update, and delete.

**Relational databases** like PostgreSQL and MySQL are more commonly used than non-relational databases like MongoDB and Neo4j because of their referential identity. They **ensure consistency and accuracy of data with the help of keys and constraints.**

Django supports multiple databases, including PostgreSQL, MariaDB, MySQL, Oracle, and SQLite. PostgreSQL and MySQL are the most commonly used. Django provides a generic way to access different databases and makes it easy to connect and work with them.

# Setting up SQLite

SQLite is the default database used in Django projects and requires no additional installation. It is set inside the **`settings.py`** file and is known as a user-friendly, zero configuration database. **This type of database is suitable for small projects or rapid prototyping, as it doesn't run as a server process and doesn't need to be started or stopped.**

# ****Using MySQL with Django****

MySQL is an open-source database and can be an alternative to SQLite when a more scalable and robust database is needed. To connect to a MySQL database, you need to provide the address, port number, and database name.

## **Steps for using MySQL with Django**

1. Install the MySQL server
2. Install the MySQL API driver (MySQL client)
3. Update MySQL settings in Django
4. Set up database tables

## ****Establishing a Connection with Django****

1. Configure parameters under the **`databases`** option in the **`settings.py`** file
2. Store database connection credentials in a separate configuration file

# Security Concerns

It's important to keep the database secure by assigning security roles and using strong usernames and passwords. The security of the database credentials is a significant risk, and as a developer, you need to be aware of potential security risks.

**Example:**

```jsx
# settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'my_database',
        'USER': 'root',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

# Conclusion

In conclusion, using Django with MySQL in a full stack application is a well-accepted industry standard due to its ease of scalability and configuration options.