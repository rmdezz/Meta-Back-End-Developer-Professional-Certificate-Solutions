# Module summary: Views

# Overview of Views

- A view is a component in the MVT (Model-View-Template) architecture that handles web requests and returns web responses
- It is just the logic that a view calls inside a method
- Examples of using views to develop a dynamic website include processing data for emails and forms, retrieving data from a database, transforming data, and rendering templates
- In Django, views are created as functions or class-based views and mapped to a URL through routing

## Creating a View in Django and Mapping it to a URL

- In Django, views are created as functions or class-based views
- To create a function-based view, simply define a function in the **`views.py`** file and add the required logic
- To map the view to a URL, it should be included in the **`urls.py`** file using the **`path()`** or **`url()`** function
- Here's an example of a simple view function in Django:

```python
from django.shortcuts import render
from django.http import HttpResponse

def home(request):
    return HttpResponse("Welcome to the home page!")
```

• The above view function can be mapped to the root URL by including the following code in the **`urls.py`** file:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
```

- In class-based views, views are created as classes that inherit from Django's built-in class-based views (CBV).
- Class-based views provide a more organized and reusable way to handle HTTP requests compared to function-based views
- Here's an example of a simple class-based view in Django:

```python
from django.views.generic import View
from django.http import HttpResponse

class HomeView(View):
    def get(self, request):
        return HttpResponse("Welcome to the home page!")
```

• The above class-based view can be mapped to the root URL by including the following code in the **`urls.py`** file:

```python
from django.urls import path
from .views import HomeView

urlpatterns = [
    path('', HomeView.as_view(), name='home'),
]
```

In this section, you learned about regular expressions in URLs and how to create different URL patterns and map a URL to a view via the view function. You also learned how to handle errors such as dealing with HTTP status responses (100, 200, 400) and error responses from the server.

```python
from django.urls import path, re_path
from . import views

urlpatterns = [
    path('product/<int:product_id>/', views.product_detail),
    re_path(r'^product/(?P<product_id>[0-9]+)/$', views.product_detail),
    path('product/search/', views.search_products),
]
```

# Best Practices

When creating views, it is important to use best practices such as code reusability and the DRY (Don't Repeat Yourself) principle. This helps to make the code more organized and easy to understand.

One way to achieve this in Django is by using class-based views. Class-based views allow for the use of object-oriented techniques such as inheritance to create views that can be reused across a project.

For example, a class-based view for handling a list of items might look like this:

```python
from django.views.generic import ListView

class ItemListView(ListView):
    model = Item
    template_name = 'item_list.html'
```

This view can then be mapped to a URL in the same way as a function-based view:

```python
from django.urls import path

from .views import ItemListView

urlpatterns = [
    path('items/', ItemListView.as_view()),
]
```

In this way, the logic for handling a list of items is encapsulated in the ItemListView class and can be reused easily in multiple places in the project.

# Request and URLs

- In Django, the HTTP request object can be used to map URLs to common CRUD operations and get information from the client
- URLs are constructed to point to specific resources or web pages on the web
- In Django, URLs are mapped to views through the **`urls.py`** file
- The URL configuration file, **`urls.py`**, is where you define the URLs for your project and map them to the corresponding views
- URLs can be mapped to views at the project and app levels
- Best practices for code reusability and dry principles are fundamental to the building blocks of Django projects

In Django, the request and response objects are used for handling HTTP requests and responses. The request object allows access to information about the current request, such as the URL and any data sent in the request. The response object is used to construct the response that will be sent back to the client.

Django uses regular expressions to match URLs to views. This allows for the creation of complex URL patterns to handle different types of requests. The **`path`** function in the **`django.urls`** module is used to define URL patterns and map them to views.

For example, a URL pattern to match a specific product by id might look like this:

Example of Using Regular Expressions in URLs:

```python
from django.urls import path

from .views import product_detail

urlpatterns = [
path('product/<int:product_id>/', views.product_detail_view, name='product_detail'),
path('product/<str:product_name>/', views.product_detail_view, name='product_detail'),
path('product/<int:year>/<int:month>/<int:day>/', views.product_archive_view, name='product_archive'),
path('product/search/', views.search_products),
]
```

In this example, the **`int:product_id`** and **`str:product_name`** parts of the URL pattern represent path parameters. 

The view function `product_detail_view` is called when the user navigates to a URL that matches this pattern. 

The `product_id` or `product_name` value is passed as an argument to the view function. 

In the second path, the **`int:year`**, **`int:month`**, and **`int:day`** parts of the URL pattern are used to capture the date and the view function `product_archive_view` is called when the user navigates to a URL that matches this pattern.