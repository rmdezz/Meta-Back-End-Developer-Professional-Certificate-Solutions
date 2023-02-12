# Exercise: Setting up the MySQL connection

# **Step 1**

To install MySQL server, download the installer appropriate for your operating system from [https://www.mysql.com/downloads/](https://www.mysql.com/downloads/).

Start the MySQL server It runs on port number 3306 by default.

To confirm it is running, start the MySQL command line client with the following command.

```jsx
mysql -u root -p
```

# **Step 2**

Activate the Python virtual environment you are using for this project, and open VS code in it. Follow the instructions from the earlier exercise.

Install the MySQL DB API Driver, **mysqlclient** from the **CMD terminal** in VS Code, use **PIP** utility with following command:

```jsx
pip3 install mysqlclient
```

# Step 3

Open the **`settings.py`** file in a VS Code window. Locate the **`DATABASES`** section. In place of the existing SQLite configuration, paste the following configuration for MySQL.

```jsx
#Settings.py 

 DATABASES = {   
    'default': {   
        'ENGINE': 'django.db.backends.mysql',   
        'NAME': 'LittleLemon',   
        'USER': 'root',   
        'PASSWORD': '',   
        'HOST': '127.0.0.1',   
        'PORT': '3306',   
        'OPTIONS': {   
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'"   
        }   
    }   
}
```

# **Step 4**

Install MySQL extension from VS Code extension marketplace.

![Untitled](Exercise%20Setting%20up%20the%20MySQL%20connection%20fa8df8ed741045e5bf144491a0f1d3fd/Untitled.png)

# Step 5

From the **CMD terminal** on Windows(Command palette in Mac OS) inside VS Code, run the migrate command.

```jsx
python manage.py migrate
```

The table structure required for the INSTALLED_APPS will be created in the MySQL database named **LittleLemon**.

# Step 6

Note that the MySQL tab appears in the file explorer bar of VS Code

![Untitled](Exercise%20Setting%20up%20the%20MySQL%20connection%20fa8df8ed741045e5bf144491a0f1d3fd/Untitled%201.png)

Click on **+**  button and connect to the database. Enter **localhost** as the domain name and null password when prompted.

Now **`localhost`** appears in the MySQL tab.

# **Step 7**

Expand the **`localhost`** to find your database – **`LittleLemon`**. Double click it to show the tables created by the migrate command

![Untitled](Exercise%20Setting%20up%20the%20MySQL%20connection%20fa8df8ed741045e5bf144491a0f1d3fd/Untitled%202.png)

# ****Conclusion****

In this exercise, you configured the Django project to use MySQL as the back-end. You also ran migration to create the table structure for the pre-installed apps in the project.