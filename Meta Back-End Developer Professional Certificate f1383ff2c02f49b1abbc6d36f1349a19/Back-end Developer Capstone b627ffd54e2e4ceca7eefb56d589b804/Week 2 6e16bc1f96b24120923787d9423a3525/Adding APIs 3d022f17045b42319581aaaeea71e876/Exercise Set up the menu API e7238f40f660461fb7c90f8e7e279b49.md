# Exercise: Set up the menu API

# Overview

In previous exercises, you have already set up a LittleLemon project that includes the Restaurant app. You have also declared the Menu and Booking models, migrated to the MySQL database.

In this exercise, you will build a REST API to perform CREATE, READ, UPDATE AND DELETE operations on the Menu model

# Scenario

You will use Django REST Framework to build the APIs in the restaurant app. You will also create the views using DRF's generic views.

# Steps

## Step 1

Install the 'rest_framework' with PIP utility while remaining in the Django virtual environment directory.

Open the command prompt in the **`LittleLemon`** directory and start VS Code.

![Screenshot 2023-02-09 at 10.52.43 PM.png](Exercise%20Set%20up%20the%20menu%20API%20e7238f40f660461fb7c90f8e7e279b49/Screenshot_2023-02-09_at_10.52.43_PM.png)

## Step 2

Open the **`settings.py`** file and add **`'rest_framework'`** in the **`LittleLemon`** project's **`INSTALLED_APPS`** list.

```jsx
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "restaurant",
    "rest_framework",
]
```

## Step 3

The **`Serializer`** in Django REST Framework converts compound data types into JSON or XML format. **ModelSerializer** is a special type of serializer that quickly creates a serializer class from the Django model fields.

The **`ModelSerializer`** class is declared in the **`rest_framework.serializers`** module.

In the app package folder, create a new file called **serializers.py** and declare the **MenuSerializer** class that subclasses **ModelSerializer**.

![Screenshot 2023-02-09 at 10.58.37 PM.png](Exercise%20Set%20up%20the%20menu%20API%20e7238f40f660461fb7c90f8e7e279b49/Screenshot_2023-02-09_at_10.58.37_PM.png)

```jsx
from rest_framework.serializers import ModelSerializer
from .models import Menu

class MenuSerializer(ModelSerializer):
    class Meta:
        model = Menu
        fields = '__all__'
```

## Step 4

Open the **`views.py`** module in the restaurant app package folder.

Declare two classes:

1. MenuItemView – inheriting the **`rest_framework.generics.ListCreateView`** class. It handles the POST and GET method calls.
2. SingleMenuItemView – inherits the **`RetrieveUpdateAPIView` and `DestroyAPIView`** classes both imported from the **`rest_framework.generics`** module. This class is responsible for processing GET, PUT and DELETE method calls.

```python
from django.shortcuts import render
from .models import Menu
from .serializers import MenuSerializer
from rest_framework import generics

# Create your views here.
def index(request):
    return render(request, 'index.html', {})

class MenuItemsView(generics.ListCreateAPIView):
    queryset = Menu.objects.all()
    serializer_class = MenuSerializer

class SingleMenuItemView(generics.RetrieveUpdateAPIView, generics.RetrieveDestroyAPIView):
    # The queryset attribute is not filtered, but the
    # DRF automatically filters it based on the pk
    # passed in the URL.
    queryset = Menu.objects.all()
    serializer_class = MenuSerializer
```

## Step 5

Define URL routes for the restaurant app's menu views in the **urls.py** file.

```jsx
#add following lines to urlpatterns list 
path('menu/', views.MenuItemsView.as_view()),
path('menu/<int:pk>', views.SingleMenuItemView.as_view()),
```

Include app URLs in the **LittleLemon** project's **urls.py** module.

```jsx
#add following line to urlpatterns list 
path('restaurant/',include('restaurant.urls')),
```

## Step 6

Run Django server, and open the URL **http://localhost:8000/restaurant/menu/items**.

This is the URL of the browsable API. Perform POST operations to add menu items. With the GET request, fetch the list of items.

[http://127.0.0.1:8000/restaurant/menu/](http://127.0.0.1:8000/restaurant/menu/)

![Screenshot 2023-02-09 at 11.15.50 PM.png](Exercise%20Set%20up%20the%20menu%20API%20e7238f40f660461fb7c90f8e7e279b49/Screenshot_2023-02-09_at_11.15.50_PM.png)

[http://127.0.0.1:8000/restaurant/menu/2](http://127.0.0.1:8000/restaurant/menu/2)

![Screenshot 2023-02-09 at 11.15.33 PM.png](Exercise%20Set%20up%20the%20menu%20API%20e7238f40f660461fb7c90f8e7e279b49/Screenshot_2023-02-09_at_11.15.33_PM.png)

# ****Conclusion****

In this exercise, you have used Django REST framework to set up the Menu API for the Restaurant app.