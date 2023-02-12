# Adding groups and users

# Introduction

- In this video, you will learn how to create a basic reservation system for the front desk of Little Lemon.
- The employees at Little Lemon have been manually entering reservation details on a sheet, but they want a more efficient way to do it.

# Setting up the [Models.py](http://Models.py) file

- Open the models.py file, which contains a reservation class with five attributes:
    - Name of the customer
    - Contact details
    - Time of arrival
    - Number of guests
    - Additional notes
- Ensure that the app is added to the installed apps list in the settings.py file
- Make the migrations

Code for [Models.py](http://Models.py) file:

```python
from django.db import models

# Create your models here.
class Reservation(models.Model):
    name = models.CharField(max_length=100, blank=True)
    contact = models.CharField('Phone Number', max_length=300)
    time = models.TimeField()
    count = models.IntegerField()
    notes = models.CharField(max_length=300, blank=True)
```

Code for INSTALLED_APPS for [settings.py](http://settings.py) file:

```python
INSTALLED_APPS = [
    "myapp.apps.MyappConfig",
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
]
```

# Creating a Super User

- Use the command **`python manage.py createsuperuser`** to create a super user
- Enter user names, email address and a password (Remember to use a strong password in production)
- Register the super user

# Working in the [Admin.py](http://Admin.py) file

- Import the reservation model
- Register the table reservation using **`admin.site.register(reservation)`**

```python
from django.contrib import admin

# Register your models here.
from myapp.models import Reservation
admin.site.register(Reservation)
```

# Using Django Administration

- Open Django at the default URL and add /admin to it
- Enter the credentials and log in
- In the my app section, click on the reservations table link
- Add some reservations using the add reservation form
    
    ![Screenshot 2023-01-28 at 10.21.22 AM.png](Adding%20groups%20and%20users%2038a1ae3010334bd9bf8aacfede30ef8f/Screenshot_2023-01-28_at_10.21.22_AM.png)
    
    ![Screenshot 2023-01-28 at 10.21.36 AM.png](Adding%20groups%20and%20users%2038a1ae3010334bd9bf8aacfede30ef8f/Screenshot_2023-01-28_at_10.21.36_AM.png)
    

# Displaying the Reservation Objects

- Override the default string representation of the object using the str method
- Define the string representation as the name of the customer
- Refresh the web page to see the changes

Code for models.py:

```python
from django.db import models

# Create your models here.
class Reservation(models.Model):
    name = models.CharField(max_length=100, blank=True)
    contact = models.CharField('Phone Number', max_length=300)
    time = models.TimeField()
    count = models.IntegerField()
    notes = models.CharField(max_length=300, blank=True)

    def __str__(self):
        return self.name
```

# Adding Users and Groups

- Go to the home link and explore the users
- Add a user by clicking on the Add user button
- Assign permissions such as active staff and super user
- Add personal info for the user
- Save the user
- Filter users according to super user status
- Create groups by selecting the groups link and clicking on the Add group button
- Assign the name of the group (e.g. staff)
- Set permissions for the staff member and save them
- Preview the table in VS Code using the SQLite Explorer
    
    ![Screenshot 2023-01-28 at 10.23.29 AM.png](Adding%20groups%20and%20users%2038a1ae3010334bd9bf8aacfede30ef8f/Screenshot_2023-01-28_at_10.23.29_AM.png)
    
    ![Screenshot 2023-01-28 at 10.23.41 AM.png](Adding%20groups%20and%20users%2038a1ae3010334bd9bf8aacfede30ef8f/Screenshot_2023-01-28_at_10.23.41_AM.png)
    

# Conclusion

- In this video, you learned how to create a basic reservation system for the front desk of Little Lemon.
- You explored how to use the admin.py file to register a model and add users and groups using Django Administration.