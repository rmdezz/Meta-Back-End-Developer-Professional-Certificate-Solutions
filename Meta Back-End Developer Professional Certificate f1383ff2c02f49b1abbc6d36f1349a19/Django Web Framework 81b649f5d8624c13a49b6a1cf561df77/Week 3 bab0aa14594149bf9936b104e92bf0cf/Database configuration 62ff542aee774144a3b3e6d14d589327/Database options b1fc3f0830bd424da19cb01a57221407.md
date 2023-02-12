# Database options

Django supports multiple databases, including SQLite, PostgreSQL, MariaDB, MySQL, and Oracle. In this text, we'll focus on connecting to a MySQL database.

# SQLite and MySQL

- SQLite is the default database for Django projects and requires no additional setup or installation.
- MySQL is a popular and widely used database and can be easily connected to a Django project by providing the database address, port number, and database name.
- The MySQL connector or driver needs to be installed to use MySQL with Django.
- The database connection is managed by the CONN_MAX_AGE parameter, which determines the time before the connection is automatically closed.

# ****Setting Up Database Connections****

To connect to a MySQL database, you need to provide the following information:

- Address of the database server
- Port number
- Database name

You also need a database driver, or connector, to translate Python queries into SQL instructions. To use MySQL, you need to install the MySQL client driver.

The connection to the database is controlled by the **`CONN_MAX_AGE`** parameter and is automatically closed after a certain time. To establish a connection, you need to configure the database settings in the **`settings.py`** file.

You can also store the database connection credentials in a separate configuration file. To maintain security, the credentials are stored outside of the Django project.

# Creating the database

- Django creates all tables based on the models from migration scripts, **but you need to manually create the database.**
- To create a database, you need a connection to the database and sufficient permissions for authentication and authorization.

# Security

- It's important to keep the database secure by using strong user names and passwords and assigning security roles.
- The database connection credentials are only accessible on the virtual machine or server where the web application is running, making it important to keep the credentials private and safe.
- As a developer, it's important to be aware of potential security risks and take the necessary measures to protect the database and its data.