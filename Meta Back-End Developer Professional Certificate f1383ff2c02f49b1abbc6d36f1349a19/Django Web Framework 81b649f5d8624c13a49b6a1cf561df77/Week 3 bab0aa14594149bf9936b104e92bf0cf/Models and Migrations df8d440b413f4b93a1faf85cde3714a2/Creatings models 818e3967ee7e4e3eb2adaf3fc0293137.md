# Creatings models

# Creating a Model in Django

## Overview

- **Building a dynamic application requires data storage, usually in the form of a database.**
- In Django, **models are used to represent a table in the database**, and are an essential part of the MVT architectural pattern.
- Models contain the essential fields and behaviors of the data being stored, and generally map to a single database table.

## Creating a Model

- In VS Code, navigate to the **`Models.py`** file in your app.
- Create a class for the model, and define variables for the attributes (e.g. name, cuisine, price).
- Assign each attribute a field of the appropriate data type (e.g. **`models.CharField`** for strings, **`models.IntegerField`** for integers).

```python
class Menu(models.Model):
    name = models.CharField(max_length=100)
    cuisine = models.CharField(max_length=100)
    price = models.IntegerField()
```

## Accessing the Model

- In the terminal, run the command **`python manage.py shell`**.
- Import the model from the **`models.py`** file using the **`from`** command.
- Run commands to perform CRUD operations on the model (e.g. **`Menu.objects.all()`** to retrieve all entries).

```python
from menuapp.models import Menu
Menu.objects.all() # Returns an empty queryset
m = Menu.objects.create(name="pasta", cuisine="Italian", price=10)
m.save()
Menu.objects.all() # Returns one entry
```

### Update a record in the database using the model

```python
# updating a record in the database
m = Menu.objects.get(name="pasta") # retrieve the pasta object
m.price = 12 # update the price
m.save() # save the changes

# To verify that the change has been made
updated_item = Menu.objects.get(name="pasta")
print(updated_item.price) # Output: 12
```

### Delete a record in the database using the model

```python
# deletion of a record in the database
m = Menu.objects.get(name="pasta")
m.delete()

# To verify that the item has been deleted
Menu.objects.filter(name="pasta").count() # Output: 0
```

## Add Model to [settings.py](http://settings.py) and Migration

- Add the model to the installed apps list in the settings.py file.
- Perform migrations using the command **`python manage.py makemigrations`** and **`python manage.py migrate`**.
- This will create a database table for the model using the built-in SQLite database.

Note that by running this commands, it creates a database table using the built-in SQLite database. and it is ready to use the model in shell or views.