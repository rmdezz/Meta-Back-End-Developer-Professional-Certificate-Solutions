# Recap: Django Routes

# Introduction

The Django framework adopts an **`MVT`** approach. 

- The model is the data layer of the application.
- The view layer is responsible for processing the request and returning the response.
- The template is the presentation layer.

Another crucial component of the Django architecture is the URL dispatcher.

![Untitled](Recap%20Django%20Routes%2046bb94cb7f634f97801606f10ab8ed64/Untitled.png)

# ****URL dispatcher****

The URL dispatcher is equivalent to Controller in the **MVC** architecture. The **urls.py** module in the Django project's package folder acts as the dispatcher.

It defines the URL patterns. Each URL pattern is mapped with a view function to be invoked when the client's request URL matches it.

The URL patterns defined in each app under the project are also included in it.

When the server receives a request in the form of a client URL, the dispatcher matches its pattern with the patterns available in the **urls.py** and routes the flow of the application toward its associated view.

Suppose a new Django project called **`littlelemon`** is created. The **`urls.py`** file in the project package shows the following code by default:

**#littlelemon/urls.py**

```jsx
from django.contrib import admin
from django.urls import path
 
urlpatterns = [
    path('admin/', admin.site.urls),
]
```

The code contains a **`urlpatterns`** list. And inside the list is a collection of URL routes where each route is constructed with the **`path()`** function.

The **`path()`** function matches a URL endpoint string with the function you want to be called.

# Create Restaurant app

As you develop an app inside the Django project, you must decide which URL patterns you'll expose to the user and which function you want to execute when each URL is requested.

The functions are defined in the **`views.py`** file inside the app package folder.

**#restaurant/views.py**

```jsx
from django.http import HttpResponse

def sayHello(request):
 return HttpResponse('Hello World')
```

Suppose that all the routes of the restaurant app will start from /restaurant.

The **`sayHello()`** view function from the code snippet in the **`views.py`** file above will be called when the user requests the URL path **`restaurant/`**.

This mapping is declared in the urls.py module of the app. And you define all the URL routes of the app in this file.

```jsx
from django.contrib import admin 
from django.urls import path 
from .views import sayHello 
  
urlpatterns = [ 
    path('', sayHello, name='sayHello'), 
]
```

# ****Include app URL configuration in project URL Configuration****

Since the **`urls.py`** file in the project package is the URL dispatcher, we need to include the routes of the app in it. Update it to contain the following code:

**#littlelemon/urls.py**

```jsx
from django.contrib import admin 
from django.urls import path, include  
 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('restaurant/', include('restaurant.urls')),
]
```

Finally, add the restaurant app to the **`INSTALLED_APPS`** list in the **`littlelemon/settings.py`** file, run the server and visit the localhost URL [http://localhost/restaurant/](http://localhost/restaurant/).

Notice that the Hello World message is displayed.