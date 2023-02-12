# Exercise: Adding unit tests

# ****Overview****

Testing is the process of validating the result of an operation against an expected output. Django’s test framework internally uses Python’s unit test package.

In this exercise, you will write the unit tests for satisfactory behavior of models and the views you have defined in the Menu API.

# Scenario

In your restaurant app, you already have built the **`Menu API`** and **`Booking API`**. You will write the model test in **test_models.py** and view test in **test_views.py files**.

# Steps

## Step 1

When you create the app, an empty **test.py** file is created in the app package folder. Go ahead and delete it.

In the project container folder, create a new folder with the name **tests**.

![Screenshot 2023-02-10 at 10.29.36 AM.png](Exercise%20Adding%20unit%20tests%2010acbdc7a5f547f3a603e2e984f7ffa5/Screenshot_2023-02-10_at_10.29.36_AM.png)

## Step 2

Open the definition of the **`Menu`** model class.

Add a **__str__()** method that returns a string representation of the model instance.

```python
#add the following method in Menu class
def __str__(self):
        return f'{self.title} : {str(self.price)}'
```

```python
class Menu(models.Model):
    title = models.CharField(max_length=255)
    price = models.DecimalField(max_digits = 10, decimal_places = 2)
    inventory = models.IntegerField()
    
    def __str__(self):
        return f'{self.title} : {str(self.price)}'
```

**Tip:** As you have made changes to the model, you must run the migrations to sync the changes.

## Step 3

Create a new file in the **tests** folder named **test-models.py**.

Import the **`TestCase`** class from the **django.tests** module.

Use it as base and declare a test class, for example, **MenuTest**.

Define an **instance** method that adds a new instance of the **Menu** model.

Call the **assertEqual()** method of the test class that compares the string representation of the newly added object with the anticipated value.

For example:

```python
from django.test import TestCase
from restaurant.models import Menu

class MenuTest(TestCase):
    def test_instance(self):
        menu = Menu.objects.create(
            title='Pizza',
            inventory=80,
            price=15.00
        )
        self.assertEqual(str(menu), "Pizza : 15.0")
```

## Step 4

Open a command terminal in VS Code. While in the project container directory, run the test with the following command:

Directory tree:

```python
LittleLemon/
    littlelemon/ (project level)
        tests/
            test-models.py
```

```python
python3 manage.py test littlelemon.tests.test-models
```

Check the result of the test if it returns as **OK**.

![Screenshot 2023-02-10 at 10.47.01 AM.png](Exercise%20Adding%20unit%20tests%2010acbdc7a5f547f3a603e2e984f7ffa5/Screenshot_2023-02-10_at_10.47.01_AM.png)

## Step 5

Open the **`test_views.py`** file in tests folder.

Write a **MenuViewTest** class that subclasses the **TestCase** class.

Use the **setup()** method to add a few test instances of the **Menu** model.

Next, add another **test_getall()** instance method to retrieve all the **Menu** objects added for the test purpose.

The retrieved objects must serialized, so make sure the method runs assertions to check if the serialized data equals the response.

```python
from django.test import TestCase
from django.urls import reverse
from rest_framework import status
from rest_framework.test import APITestCase
from restaurant.models import Menu
import json
from restaurant.serializers import MenuSerializer

class MenuViewTest(APITestCase):
    def setUp(self):
        self.menu_item1 = Menu.objects.create(title = "Pizza", price = 12.99, inventory = 5)
        self.menu_item2 = Menu.objects.create(title = "Burger", price = 8.99, inventory = 10)
        
    def test_getall(self):
        url = reverse('MenuItemsView') # takes a view name as an argument and returns the corresponding URL
        response = self.client.get(url) # sends a GET request to the URL returned by 'reverse' and stores the response in the 'response' variable
        self.assertEqual(response.status_code, status.HTTP_200_OK)
        
        menu_items = Menu.objects.all() # gets a queryset of all 'Menu' objects from the database
        serializer = MenuSerializer(menu_items, many = True) # serializes the queryset of 'Menu' objects into a JSON-like format
        self.assertEqual(response.data, serializer.data)
```

Run the test again with the command **python manage.py test** and verify if the test returns as **OK**.

![Screenshot 2023-02-10 at 1.06.17 PM.png](Exercise%20Adding%20unit%20tests%2010acbdc7a5f547f3a603e2e984f7ffa5/Screenshot_2023-02-10_at_1.06.17_PM.png)

# Conclusion

In this exercise, you created and ran the unit tests to test the model and view for the **Menu** API.