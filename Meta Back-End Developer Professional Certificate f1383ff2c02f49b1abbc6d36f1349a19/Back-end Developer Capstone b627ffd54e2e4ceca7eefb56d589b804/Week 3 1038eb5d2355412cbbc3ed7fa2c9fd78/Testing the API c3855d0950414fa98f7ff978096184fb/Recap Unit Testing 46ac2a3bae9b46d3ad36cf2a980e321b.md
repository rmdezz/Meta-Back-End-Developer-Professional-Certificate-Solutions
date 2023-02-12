# Recap: Unit Testing

# ****Introduction****

**Testing is a vital part of the software development process.**

Before pushing the application to the production stage, validating it against the expected output is essential.

Before you commit any change to the source code, it must be verified that your changes don't affect the application's behavior.

A developer is always well advised to adopt an approach of test-driven development.

Django's testing framework provides the API to test your code and check if it is doing as expected.

The test framework of Django is built upon the unit test package bundled with Python's standard library.

# ****Prerequisites****

- Install Django and Django REST Framework in the current Python environment
- Create a Django project named **LittleLemon** with **django-admin** command
- Inside it, create a Django app with the name **LittleLemonAPI**
- Add the **'rest_framework'** and **'LittleLemonAPI'** to the **INSTALLED_APPS** list
- Run the **migrate** command

# ****Model****

Define the **`MenuItem`** model in **LittleLemonAPI/models.py** file using the following code:

```python
from django.db import models  

# Create your models here.  

class MenuItem(models.Model):  

    title = models.CharField(max_length=255)  
    price = models.DecimalField(max_digits=6, decimal_places=2)  
    inventory = models.SmallIntegerField()  

    def get_item(self):  
        return f'{self.title} : {str(self.price)}'
```

# ****Serializer****

Serialization is crucial in building an API with the Django REST Framework. It serializes the model instances into JSON format.

Use the **`ModelSerializer`** class to declare a **serializer** for the **MenuItem** model. Add the following code in the **LittleLemonAPI/serializers.py** file.

```python
from rest_framework import serializers 
from .models import MenuItem  

class MenuItemSerializer(serializers.ModelSerializer): 

    class Meta: 
        model = MenuItem 
        fields = ['id','title','price','inventory']
```

# ****Views****

The next step is to provide the app with the view definitions. **DRF** has generic view classes. The **ListCreateAPIView** handles the POST and GET methods to add a model instance and retrieve all instances. Use it as a base for **MenuItemsView** class.

**LittleLemonAPI/views.py**

```python
from rest_framework import generics 
from .models import MenuItem 
from .serializers import MenuItemSerializer 

# Create your views here. 
class MenuItemsView(generics.ListCreateAPIView): 
    queryset = MenuItem.objects.all() 
    serializer_class = MenuItemSerializer
```