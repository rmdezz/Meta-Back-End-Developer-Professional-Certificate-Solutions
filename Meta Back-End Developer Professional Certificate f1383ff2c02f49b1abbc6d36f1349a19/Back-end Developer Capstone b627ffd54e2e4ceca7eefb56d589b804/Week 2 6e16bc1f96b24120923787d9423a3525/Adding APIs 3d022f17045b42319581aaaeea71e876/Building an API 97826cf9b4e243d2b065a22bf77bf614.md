# Building an API

Django is a powerful web framework that can be used to build web applications with ease. 

In addition to its templating system that allows for the creation of dynamic HTML pages, Django can also be used to build **REST APIs** that return JSON or XML responses. 

The Django REST Framework (DRF) provides a convenient wrapper around the core Django package to make it easier to build REST APIs.

In this guide, we will explore the steps to build REST APIs for performing CRUD operations on the menu and booking models.

# Step 1: Install Django Rest Framework

Use the following command to install Django REST Framework:

```jsx
pip install djangorestframework
```

or

```jsx
pipenv install djangorestframework
```

# Step 2: Add DRF to installed apps

Add **`rest_framework`** to the list of installed apps in the project's **`settings.py`** file:

```jsx
INSTALLED_APPS = [    ...    'rest_framework',    'restaurant',    ...]
```

# Step 3: Declare models and migrate to database

Ensure that the menu model and booking model classes are declared in the **`models.py`** file and that they have been migrated to the database.

# Step 4: Create serializers

In order to serialize the model data to JSON, you will need to create serializer classes. Import the **`serializers`** class from **`rest_framework`** and declare its subclass corresponding to the models in the app. Save these classes in the **`serializers.py`** file.

```jsx
from rest_framework import serializers
from .models import Menu, Booking

class MenuSerializer(serializers.ModelSerializer):
    class Meta:
        model = Menu
        fields = '__all__'

class BookingSerializer(serializers.ModelSerializer):
    class Meta:
        model = Booking
        fields = '__all__'
```

# Step 5: Create views

Once the code to handle serialization is set up, you can create views for the API. This guide will demonstrate the use of class-based views, but it is also possible to use function-based views.

**For example:**

```jsx
from rest_framework import generics
from .models import Menu, Booking
from .serializers import MenuSerializer, BookingSerializer

class MenuList(generics.ListCreateAPIView):
    queryset = Menu.objects.all()
    serializer_class = MenuSerializer

class MenuDetail(generics.RetrieveUpdateDestroyAPIView):
    queryset = Menu.objects.all()
    serializer_class = MenuSerializer

class BookingList(generics.ListCreateAPIView):
    queryset = Booking.objects.all()
    serializer_class = BookingSerializer

class BookingDetail(generics.RetrieveUpdateDestroyAPIView):
    queryset = Booking.objects.all()
    serializer_class = BookingSerializer
```

# Step 6: Update URL configuration

Finally, update the URL configuration of the app as well as the project. In the **`restaurant`** app's **`urls.py`** file, merge the URL conf of the app with that of the project.

Here's an example of how to update the URL configuration in the app's **`urls.py`** file:

```jsx
from django.urls import path, include

urlpatterns = [
    path('menu/', include('restaurant.urls')),
]
```

And here's an example of how to update the URL configuration in the project's **`urls.py`** file:

```jsx
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('restaurant.urls')),
]
```

# Step 7: ****Run the Server and Test the API****

Finally, run the server and test the API with a HTTP client such as Postman, HTTPie, or Insomnia.

Here's an example of how to run the server:

```jsx
(LittleLemon) (base) ricardo@Ricardos-iMac LittleLemon % python3 manage.py runserver
```

And here's an example of how to test the API using HTTPie:

```jsx
(LittleLemon) (base) ricardo@Ricardos-iMac LittleLemon % http GET http://localhost:8000/menu/
HTTP/1.1 200 OK
...
[
    {
        "id": 1,
        "title": "Spaghetti Bolognese",
        "price": "10.00",
        "inventory": 100
    },
    {
        "id": 2,
        "title": "Pizza Margherita",
        "price": "12.00",
        "inventory": 200
    }
]
```

# Conclusion

With these steps, you'll be able to build REST APIs for performing CRUD operations on the menu and booking models in Django.