# Function and class-based views

In this video, you'll learn about the benefits of using class-based views in Django Rest Framework (DRF) and how to create and implement them.

# Advantages of Class-Based Views

- Less code duplication
- Write less code
- Ability to extend and add features
- Ability to write specific methods for each HTTP request

# Creating Class-Based Views

To create a class-based view in DRF, you must extend the **`APIView`** class from the **`rest_framework`** module and import the **`Response`** class.

Here's an example of creating a class-based view named **`BookList`**:

```bash
from rest_framework.response import Response
from rest_framework.views import APIView

class BookList(APIView):
    def get(self, request, *args, **kwargs):
        return Response({"message": "list of the books"}, status.HTTP_200_OK)
```

# Mapping Class-Based Views in URLs

To map a class-based view in the URL patterns, simply add the class to the **`urlpatterns`** array in the **`urls.py`** file.

Here's an example of mapping the **`BookList`** class in `**urls.py**` app’s file:

```bash
from django.urls import path
from .views import BookList

urlpatterns = [
    path("books/", BookList.as_view(), name="books"),
]
```

In **`urls.py`** project’s file:

```bash
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("api/", include('BookListAPI.urls')),
]
```

# Accessing Query String Parameters

To access query string parameters, you can use the **`request.GET.get()`** method. Here's an example of accessing the **`author`** parameter in the **`get`** method of the **`BookList`** class:

```bash
class BookList(APIView):
    def get(self, request, *args, **kwargs):
        author = request.GET.get("author", None)
        if author:
            return Response({"message": "list of the books by " + author}, status.HTTP_200_OK)
				return Response({"message": "list of the books"}, status.HTTP_200_OK)
```

# Accepting Payload in POST Requests

To accept payload in POST requests, you can use the **`request.data.get()`** method. Here's an example of accepting the **`title`** parameter in the **`post`** method of the **`BookList`** class:

```bash
class BookList(APIView):
    def post(self, request, *args, **kwargs):
        title = request.data.get("title", None)
        return Response({"title": request.data.get('title')}, status.HTTP_201_CREATED)
```

# Accessing Primary Key in Class-Based Views

To access the primary key in class-based views, you can add an extra argument for the primary key in the method and access it using the method arguments.

Here's an example of accessing the primary key in the **`get`** method of a class named **`Book`**:

```bash
class Book(APIView):
    def get(self, request, pk, *args, **kwargs):
        return Response({"message": "single book with id " + str(pk)}, status.HTTP_200_OK)
```

# PUT Requests in Class-Based Views

To handle PUT requests in class-based views, you need to add a **`put`** method in your class. This method will also accept an extra argument **`pk`** to access the primary key of the book. 

To access the request parameters in a PUT request, you can use **`request.data.get()`**:

```bash
class Book(APIView):
    def get(self, request, pk):
        return Response({"message": "single book with id " + str(pk)}, status.HTTP_200_OK)

    def put(self, request, pk):
        return Response({"title": request.data.get('title')}, status.HTTP_200_OK)
```

In the URL configuration, you need to map this new class to a URL pattern and include the primary key in the URL. For example:

```bash
urlpatterns = [
    path('books/', views.BookList.as_view()),
    path('books/<int:pk>', views.Book.as_view()), #this
]
```

Now, to test this endpoint, you can visit the URL **`http://localhost:8000/api/books/1`** and send a JSON payload using a PUT request:

```bash
{
    "title": "New Title"
}
```

After sending the request, you should see the updated book in the API response.

# Throttling and Authentication in Class-Based Views

The API View class in DRF also provides options for throttling and authentication. 

Throttling allows you to limit the number of requests a client can make to your API in a given time period. 

Authentication, on the other hand, allows you to ensure that only authenticated users can access your API endpoints. You'll learn more about these concepts in later sections of the course.

# Conclusion

In conclusion, class-based views in DRF provide a clean and organized way to handle different types of HTTP requests and can help you reduce code duplication. Additionally, they provide options for throttling and authentication to secure your API endpoints.