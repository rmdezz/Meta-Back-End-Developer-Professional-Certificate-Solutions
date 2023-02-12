# Exercise: Setting up the models

# ****Overview****

By now, you have created a back-end Django application containing a project called **`LittleLemon`**, and an app called **`Restaurant`**. You have also configured the application to use a MySQL database.

In this exercise, you will create the Menu and Booking models for the Restaurant app and migrate them to the MySQL database tables of the same name.

# ****Scenario****

By the end of this project, you will have built REST APIs for ordering food using the Menu API and reserving the table using the Booking API.

You will build these APIs based on the Menu and Booking models using the model schema provided to you.

# **Booking table**

![Untitled](Exercise%20Setting%20up%20the%20models%20840866685a484017bc9be7c682d97601/Untitled.png)

# **Menu table**

![Untitled](Exercise%20Setting%20up%20the%20models%20840866685a484017bc9be7c682d97601/Untitled%201.png)

# Prerequisites

Ensure that you have created a Django virtual environment, and inside it, a project called **`LittleLemon`**. Inside the project, make sure you have an app called **`Restaurant`**.

You also need to have the MySQL server running with the **`LittleLemon`** database.

# Steps

## **Step 1: Declare Menu and Booking models**

Refer to the table schema for the **Menu** and **Booking** tables provided to you. Declare the **menu** and **booking** model classes with matching attributes.

You must save the code for these classes in the **models.py** file under the **restaurant** app package folder.

```jsx
class Booking(models.Model):
    name = models.CharField(max_length=255)
    no_of_guests = models.IntegerField(max_length=6)
    booking_date = models.DateTimeField()

class Menu(models.Model):
    title = models.CharField(max_length=255)
    price = models.FloatField(max_digits = 10, decimal_places = 2)
    inventory = models.IntegerField()
```

## Step 2: Perform migrations

First, run the **`makemigrations`** command of the **manage.py script**.

Then run the command **`python manage.py migrate`**.

The corresponding tables will be created in the database.

Confirm that tables are created using the MySQL browser extension you installed earlier in VS Code.

![Screenshot 2023-02-09 at 9.10.44 PM.png](Exercise%20Setting%20up%20the%20models%20840866685a484017bc9be7c682d97601/Screenshot_2023-02-09_at_9.10.44_PM.png)

![Screenshot 2023-02-09 at 10.06.35 PM.png](Exercise%20Setting%20up%20the%20models%20840866685a484017bc9be7c682d97601/Screenshot_2023-02-09_at_10.06.35_PM.png)

## Step 3: **Register the models in admin module**

Open the **`admin.py`** file and register the **`Menu`** and **`Booking`** models with the admin site using the **`admin.site.register()`** method.

## Step 4: **Add data in models**

Login to the admin panel with the superuser created earlier.

```jsx
python3 manage.py createsuperuser
```

Add some data in Menu and Booking models using the admin interface.

## Step 5: **Check the data in VS Code**

Refresh the MySQL browser in VS Code to display the data added through the admin interface.

![Screenshot 2023-02-09 at 10.13.33 PM.png](Exercise%20Setting%20up%20the%20models%20840866685a484017bc9be7c682d97601/Screenshot_2023-02-09_at_10.13.33_PM.png)

# Conclusion

In this exercise, you successfully declared the models for restaurant app and migrated to the MySQL database.