# Installing and setting up DRF

In this video, you'll learn how to install and configure DRF in a Django project with ease. You'll have the option to use pip or pipenv to manage the dependencies.

## Installing DRF

1. Start by opening the terminal and navigating to your project directory.
2. If using pipenv, run the following commands:

```bash
pipenv install django
pipenv shell
pipenv install djangorestframework
```

1. If using pip, run the following command:

```bash
pip or pip3 install djangorestframework
```

## Creating a Django project

In the terminal, run the following commands:

```bash
django-admin startproject BookList .
python manage.py startapp BookListAPI
```

## Configuring DRF

1. Open the **`settings.py`** file in the project directory and find the **`INSTALLED_APPS`** section.
2. Add **`rest_framework`** and **`BookListAPI`** to the end of the list.

## Creating an API Endpoint

1. In the **`views.py`** file of the **`BookListAPI`** app, add the following code:

```bash
from django.shortcuts import render
from rest_framework.response import Response
from rest_framework import status
from rest_framework.decorators import api_view

# Create your views here.
@api_view()
def books(request):
    return Response("list of books", status=status.HTTP_200_OK)
```

1. Create a new file called **`urls.py`** in the **`BookListAPI`** directory and add the following code:

```bash
from django.urls import path
from . import views

urlpatterns = [
    path("books/", views.books),
]
```

1. In the project's main **`urls.py`** file, add the following line to link the newly created books endpoint:

```bash
from django.urls import include

urlpatterns = [
    path('api/', include('BookListAPI.urls')),
]
```

## Testing the API Endpoint

1. Run the migrate command in the terminal:

```bash
python3 manage.py migrate
```

1. Start the web server using the following command:

```bash
python3 manage.py runserver
```

1. Access the books endpoint by making an HTTP GET request to **`http://127.0.0.1:8000/api/books`** using a tool like Insomnia.
    
    ![Screenshot 2023-02-01 at 12.58.22 PM.png](Installing%20and%20setting%20up%20DRF%20a60016eb19114e57ba89b042da866170/Screenshot_2023-02-01_at_12.58.22_PM.png)
    
    ![Screenshot 2023-02-01 at 12.58.33 PM.png](Installing%20and%20setting%20up%20DRF%20a60016eb19114e57ba89b042da866170/Screenshot_2023-02-01_at_12.58.33_PM.png)
    
2. If you want to accept other HTTP methods like POST, PUT, or DELETE, you need to define them in the API view decorator. For example, to accept POST requests, add **`['POST']`** in the **`@api_view`** decorator.
    
    ![Screenshot 2023-02-01 at 12.59.18 PM.png](Installing%20and%20setting%20up%20DRF%20a60016eb19114e57ba89b042da866170/Screenshot_2023-02-01_at_12.59.18_PM.png)
    
    ![Screenshot 2023-02-01 at 1.05.56 PM.png](Installing%20and%20setting%20up%20DRF%20a60016eb19114e57ba89b042da866170/Screenshot_2023-02-01_at_1.05.56_PM.png)