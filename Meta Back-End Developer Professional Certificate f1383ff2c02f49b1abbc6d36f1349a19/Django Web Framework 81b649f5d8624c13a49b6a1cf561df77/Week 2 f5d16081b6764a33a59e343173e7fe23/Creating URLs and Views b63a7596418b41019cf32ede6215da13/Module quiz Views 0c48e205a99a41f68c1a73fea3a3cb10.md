# Module quiz: Views

1. To add a URL pattern with regex, you use the **re_path()** function instead of the **path()** function.
    
    ```python
    Answer: True
    ```
    
    **Explanation:**
    
    ```python
    from django.urls import path, re_path
    from . import views
    
    urlpatterns = [
        path('product/<int:product_id>/', views.product_detail),
        re_path(r'^product/(?P<product_id>[0-9]+)/$', views.product_detail),
        path('product/search/', views.search_products),
    ]
    ```
    
2. Which of the following sentences about the **path()** function is correct? Select all that apply.
    1. The **path()** function is used to define a URL pattern.
    2. The **path()** function is defined in the **django.urls** module.
    3. The **path()** function returns the path of the Django app.
    4. The URL string parameter of the **path()** function captures query parameters from the URL.
    
    ```python
    Answer: a, b
    ```
    
    **Explanation:**
    
    1. The path() function is a function provided by Django. It is used to define URL patterns for a Django app.
    2. The path() function is defined in the django.urls module.
    3. The path() function returns a RegexURLResolver, which can be passed to the urlpatterns variable in the urls.py file of the app. When a request matches the URL pattern, the corresponding view function is called with the captured variables as keyword arguments. Therefore, it does not returns the path of the Django app.
    4. The URL string parameter of the path() function captures path parameters from the URL, not query parameters, which are passed as part of the request in the query string (after the '?' character)
    
    3. Complete the sentence. The path converters capture _____ from the URL.
    
    1. Query parameters
    2. URL parameters
    3. Path parameters
    4. Body parameters
    
    ```python
    Answer: c
    ```
    
    **Explanation:**
    
    Explanation: The path() function in Django's url dispatcher is used to define a URL pattern. In this URL pattern, one can capture different types of parameters from the URL. The path converters, for example, <**int:product_id>**, capture path parameters, which are specified in the URL string, from the URL. These parameters are then passed to the view function specified in the path() function as arguments, and can be accessed within the function to perform specific operations.
    
    ```python
    path('/products/<int:product_id>/', views.product_detail)
    ```
    
    1. The **request.user** attribute contains the information of the current user.
    
    ```python
    Answer: True
    ```
    
    **Explanation:**
    
    The request object in Django contains all the information related to a client's request, such as headers, body, cookies, etc. One of the attributes of the request object is user, which represents the user that made the request. It contains information such as the user's ID, username, email, and any other data you might have stored in your authentication system.
    
    5.  Complete the following sentence. The HTTP status code starting with 5 implies that:
    
    1. The request has been received and is under process.
    2. The action has been successfully completed.
    3. There is a client-side error.
    4. The server has encountered an error.
    
    ```python
    Answer: c
    ```
    
    **Explanation:**
    
    Response status codes beginning with the digit "5" **indicate cases in which the server is aware that it has encountered an error or is otherwise incapable of performing the request**.
    
    1. What are the important features of a class-based view? Select all that apply.
        1. Class-based views are reusable.
        2. A class-based view implements different methods for each HTTP method.
        3. A class-based view subclasses the django.view.View base class.
        4. The as_view() method maps a URL to a class-based view.
        
        ```python
        Answer: a, b, c, d
        ```
        
        Class-based views are a different way of creating views in Django that offer some advantages over function-based views. 
        
        One of the key features of a class-based view is that it subclasses the django.view.View base class, which means it can inherit a lot of common behavior and methods. This makes it reusable, as you can create a view class and use it across your application without repeating the same code. Another important feature is that class-based views implement different methods for each HTTP method, such as get(), post(), etc., making it easy to separate the logic for different types of requests. Finally, the as_view() method is used to map a URL to a class-based view, which makes it easy to use the same class in different parts of your application.
        
    2. The **Http404** response is a convenient alternative for an **HttpResponse**.
    
    ```python
    Answer: True
    ```
    
    **Explanation:**
    Http404 is a specific response that Django raises when it cannot find a matching URL for a request. It tells the client that the requested resource was not found. On the other hand, HttpResponse is a general-purpose response that can be used to return any type of data to the client. It's not a convenient alternative for Http404, but for other types of responses.
    
    1. Complete the following sentence. The URL name is _______________.
    Select all that apply.
        1. passed as the **name** parameter in the **path()** function.
        2. an optional parameter passed inside the **path()** function.
        3. used to define URL namespace.
        4. used by the **reverse()** function to fetch the URL mapped with the view function.
        
        ```python
        Answer: a, b, c, d
        ```
        
        **Explanation:**
        
        The URL name is used to define URL namespace, is an optional parameter passed inside the path() function, passed as the name parameter in the path() function, and used by the reverse() function to fetch the URL mapped with the view function.
        
    2. Can you define views in the **views.py** file in the projects folder?
    
    ```python
    Answer: True
    ```
    
    1. Complete the following sentence. To override the default error view, _______________.
        
        Select all that apply.
        
        1. you should define the custom error handler view in the app's **views.py** file.
        2. specify the appropriate handler in the project's **URLConf**
        3. define the custom view in the project folder.
        4. there's no need to override the default error views.
        
        ```python
        b, c
        ```