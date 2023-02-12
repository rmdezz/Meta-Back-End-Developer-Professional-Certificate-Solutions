# Exercise: Setting up the static routes

# Overview

With Django’s powerful Templating language, you can render the HTML pages as the response to a client.

The default Django project template installs the **`staticfiles`** app. It provides the functionality for including static assets such as images, JavaScript and CSS files on the web page.

In this exercise, you will define a URL route whose mapped view renders a web page. You will also include an image in the HTML script of the web page.

You can find the resources for these static assets from the link below.

[_ozfC8MeRya4iwepjfZtXg_806971f605b842c4a88cff4cd0b7b6e1_Static-routes-assets.zip](Exercise%20Setting%20up%20the%20static%20routes%20a5032249653b4c74a2866354bd44d2ad/_ozfC8MeRya4iwepjfZtXg_806971f605b842c4a88cff4cd0b7b6e1_Static-routes-assets.zip)

# Scenario

You will be displaying the home page of your web app for your Capstone project application.

# Prerequisites

You have already installed the Django framework in a Python virtual environment. You have also created a Django project with **`LittleLemon`** as its name, and it has a Django app called **`restaurant`**.

# Steps

## Step 1: **Create a templates directory**

The project package folder and the app package folder both are created inside the outer folder which is identified as **`BASE_DIR`**. Inside this **`BASE_DIR`**  create a template directory/folder named **`templates`**.

## **Step 2: Include the templates directory in settings.py**

In VS Code, go to the **`TEMPLATES`** section in the **`settings.py`** file and ensure that the templates directory created in the above step is in the list of the **DIRS** attribute.

```jsx
#Include 'templates' in 'DIRS' attribute
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

## Step 3: Create index.html

Inside the templates folder, create a new file called **`index.html`** and put the following script in it.

```jsx
<html>
   <head>
      <title>Capstone Project</title>
   </head>
   <body>
      <h1 style="text-align:center;">Welcome ToLittleLemon Restaurant</h1>
   </body>
</html>
```

## Step 4: **Define index view**

Open the **`views.py`** file from the **`restaurant`** folder. Add the following function:

```jsx
from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request, 'index.html', {})
```

## Step 5: **Add the URL route**

Open the urls.py file from the **`restaurant`** folder. Make sure that the following path is added to the **`urlpatterns`** list.

```jsx
#define URL route for index() view
from django.urls import path
from . import views

urlpatterns = [
    . . . ,
    path('', views.index, name='index')
]
```

## Step 6: **Update URLConf**

Open the **`urls.py`** file from the **`Littlelemon`** folder. Include the URL patterns of the **`restaurant`** app in it.

```jsx
#update URLConf by including URL patterns of restaurant app
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
   path('admin/', admin.site.urls),
   path('restaurant/', include(restaurant.urls'))
]
```

## Step 7: Visit the home page

Run the Django server with the **manage.py** script and visit the **http://localhost:8000/restaurant/** URL.

![Untitled](Exercise%20Setting%20up%20the%20static%20routes%20a5032249653b4c74a2866354bd44d2ad/Untitled.png)

## Step 8: **Save the LittleLemon.png image**

All the static assets must be placed in the **restaurant/static/restaurant** folder. Put the littlelemon.png file here.

![logo.png](Exercise%20Setting%20up%20the%20static%20routes%20a5032249653b4c74a2866354bd44d2ad/logo.png)

## Step 9: **add the static tag in index.html**

Modify the **`index.html`** file to include the following statements.

```jsx
<!--add this template tag-->
{% load static %}
<img src="{% static 'restaurant/littlelemon.png' %}">
```

## Step 10: Refresh the home page

You should see the image rendered on the browser.

If you can’t, then add this to the [settings.py](http://settings.py) file 

```jsx
STATICFILES_DIRS = [
    "static",
]
```

Directory tree should look like:

```jsx
BASE_DIR/
├── project/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── app/
│   ├── __init__.py
│   ├── models.py
│   ├── urls.py
│   └── views.py
├── templates/
│   └── template.html
└── static/
    └── restaurant/
        └── logo.png
```

# Conclusion

In this exercise, you successfully rendered a web page with a static image file.