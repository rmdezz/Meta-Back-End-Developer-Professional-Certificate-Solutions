# What you know about URLs and Routes

In this section, you will review the concepts of URLs, routes, and views in Django. Django uses route-based URLs instead of file-based URLs.

# ****URL Paths****

The part of the URL after the domain name is called the URL path and may contain path and query parameters. For example: **`littlelemon.com/menu/2`** where **`menu`** is the path and **`2`** is the path parameter.

HTTP clients, such as a browser or cURL, send URL requests with HTTP GET, POST, PUT, or DELETE methods.

# URLConf

A Django project uses the URLConf to handle client requests. The variable **`ROOT_URLConf`** in the project's **`settings.py`** file sets the URLConf. The **`URLs.py`** module in the project package acts as the URL dispatcher and defines a **`URL patterns`** list of routes created using the **`path`** function from the **`django.urls`** module.

```jsx
# Example of URLConf in settings.py
ROOT_URLConf = 'project.URLs'
```

```jsx
# Example of URL dispatcher in URLs.py
from django.urls import path

from . import views

URLpatterns = [
    path('menu/<int:menu_id>/', views.menu_detail),
    path('register/', views.register),
    path('login/', views.login),
    # ...
]
```

# ****App URLConf****

When you create an app inside the Django project, you create another **`urls.py`** file inside the app folder and define a **`URL patterns`** list. Each item in the list is a route, and the **`path`** function binds a URL path to a view function. 

Add the app to the **`installed apps`** list in the **`settings.py`** file, and the URL configuration of the app will be included in the project's URL configuration.

```jsx
# Example of installed apps in settings.py
INSTALLED_APPS = [
    # ...
    'app',
    # ...
]
```

```jsx
# Example of app URLConf in urls.py
from django.urls import path

from . import views

URLpatterns = [
    path('menu/<int:menu_id>/', views.menu_detail),
    path('register/', views.register),
    path('login/', views.login),
    # ...
]
```

# Views

When a URL is received from a client, Django matches it with the URL patterns defined in the URLConf. When the first matching URL pattern is found, Django imports the associated view, either a Python function or a view class defined in the **`views.py`** file inside the app folder. 

The view receives the HTTP request object and any path parameters captured by the URL pattern definitions, processes the request, interacts with a model if necessary, and returns its HTTP response directly or by rendering a template.

```jsx
# Example of a view function in views.py
from django.shortcuts import render

def menu_detail(request, menu_id):
    menu = get_object_or_404(Menu, id=menu_id)
    return render(request, 'menu_detail.html', {'menu': menu})
```

# Error handling

If the URL doesn't match any of the patterns in the URLConf, Django invokes the corresponding error handling view.

# Static Assets

Web applications often need to render static content, such as images, JavaScript code, or CSS styles. These static assets are placed in a designated static folder. 

The **`settings.py`** file defines a **`static URL`** variable, usually set to **`static`**, and a **`static files DIRS`** variable to tell Django where to look for the static assets. The **`load static`** template tag is used to fetch the URL of the static asset rendered by the template.

```jsx
# Example of static URL in settings.py
STATIC_URL = '/static/'

# Example of static files DIRS in settings.py
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static'),
]
```

```jsx
{% load static %}

<img src="{% static 'image.jpg' %}" alt="Image">
<link rel="stylesheet" href="{% static 'style.css' %}">
<script src="{% static 'script.js' %}"></script>
```

# Conclusion

In this section, you reviewed the key concepts of URLs, routes, and views in Django.