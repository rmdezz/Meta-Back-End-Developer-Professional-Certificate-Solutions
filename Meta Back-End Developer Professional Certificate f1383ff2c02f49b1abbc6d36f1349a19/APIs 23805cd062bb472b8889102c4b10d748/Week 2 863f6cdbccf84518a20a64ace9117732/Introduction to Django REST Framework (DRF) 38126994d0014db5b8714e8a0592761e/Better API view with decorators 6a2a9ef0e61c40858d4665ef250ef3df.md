# Better API view with decorators

So far in this course, you've been using the API View Decorator in your Django Rest Framework (DRF) apps. But what exactly is the API View Decorator and why is it so useful in DRF? In this article, we'll explore the benefits of using the API View Decorator and how it makes API development in Django more effective.

# Using the API View Decorator

To use the API View Decorator, you'll need to import the **`api_view`** function from the **`rest_framework.decorators`** module and add it before the function definition in your views.py file. 

For example:

```bash
from rest_framework.decorators import api_view

@api_view()
def books(request):
    return Response("list of books", status=status.HTTP_200_OK)
```

# Benefits of using the API View Decorator

There are several benefits to using the API View Decorator in your DRF apps. Let's take a closer look at some of the most significant benefits:

## Browsable API Interface

One of the most significant benefits of using the API View Decorator is that it turns your standard API output into a polished and user-friendly browsable API interface. To use this feature, you'll need to use the **`Response`** class from the **`rest_framework.response`** module. Here's an example:

```bash
from rest_framework.response import Response

@api_view()
def books(request):
    return Response("list of books", status=status.HTTP_200_OK)
```

## Specifying Supported HTTP Methods

The API View Decorator also allows you to specify which HTTP methods your function should support. You can pass an array of HTTP method names to the **`api_view`** function. 

For example:

```bash
@api_view(['GET', 'POST'])
def books(request):
    if request.method == 'POST':
        # handle post request
        return Response("POST request received", status=status.HTTP_200_OK)
    else:
        # handle get request
        return Response("list of books", status=status.HTTP_200_OK)
```

## Throttling and Rate-Limiting

The API View Decorator also allows you to implement Throttling or Rate-limiting, which means you can define how many times someone can access an API endpoint in a given period. This is especially useful for protecting your API from excessive usage. You'll learn more about Throttling and Rate-limiting later in this course.

## Authenticating API Endpoints

The API View Decorator also helps you to authenticate your API endpoints so that only authenticated users can access them. This is a neat feature that helps to keep your API secure.

# Conclusion

In this article, you learned about the benefits of using the API View Decorator in DRF. From converting the standard API output into a browsable API interface to specifying supported HTTP methods, Throttling, and Rate-limiting, the API View Decorator is a powerful tool that makes API development in Django more effective.