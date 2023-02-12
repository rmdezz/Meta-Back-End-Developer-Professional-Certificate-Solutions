# API throttling for class-based views

# Introduction

You already learned about the basics of rate limiting or throttling earlier in the course. But, in this reading, you will learn how to quickly implement throttling in class-based views. You will also learn about how some real-world services use this API throttling to protect their API endpoints from abuse.

# Project scaffolding

Use a class-based view to extend the **`ModelViewSet`** to quickly implement a functional CRUD API endpoint for the menu items. To create this class-based view add these lines in the **views.py** file.

```python
from rest_framework.response import Response 
from rest_framework import viewsets 
from .models import MenuItem 
from .serializers import MenuItemSerializer

class MenuItemsViewSet(viewsets.ModelViewSet):
    queryset = MenuItem.objects.all()
    serializer_class = MenuItemSerializer
```

Open the **`urls.py`** file and map this **`MenuItemViewSet`** class to the **`menu-items`** API endpoint. Map only the **`GET`** methods.

```python
from django.urls import path 
from . import views 

urlpatterns = [ 
    path('menu-items',views.MenuItemsViewSet.as_view({'get':'list'})),
    path('menu-items/<int:pk>',views.MenuItemsViewSet.as_view({'get':'retrieve'})),
]
```

Now you can list all menu items by visiting **`http://127.0.0.1:8000/api/menu-items`** and any single menu item by visiting **`http://127.0.0.1:8000/api/menu-items/1`**.

# ****Add support for throttling****

DRF comes with excellent throttling classes that you can use straight out of the box. To do this, add the following lines in the **settings.py** in the **REST_FRAMEWORK** section.

```python
'DEFAULT_THROTTLE_CLASSES': [
        'rest_framework.throttling.AnonRateThrottle',
        'rest_framework.throttling.UserRateThrottle'
],
```

Now you can implement throttling in your API project.

# ****Throttling for class-based views****

Class-based views don’t use the **throttle_classes** decorator like function-based views. To use throttling, you need to pass the throttle classes to a public class property called throttle_classes. First import the necessary classes in the **views.py** file.

```python
from rest_framework.throttling import UserRateThrottle, AnonRateThrottle
```

Then create a public property called **throttle_classes** with either one or both of these two classes, **UserRateThrottle** or **AnonRateThrottle**.

```python
class MenuItemsViewSet(viewsets.ModelViewSet):
    throttle_classes = [AnonRateThrottle, UserRateThrottle]
    queryset = MenuItem.objects.all()
    serializer_class = MenuItemSerializer
```

Now the **`menu-items`** API endpoints will be throttled for both anonymous and authenticated users. You can define the throttling rate for both in the **settings.py** file. If you want to limit the API calls to 5 per minute for anonymous users and 10 per minute for authenticated users, then add the following lines in the **REST_FRAMEWORK** section, as you learned in a previous video.

```python
'DEFAULT_THROTTLE_RATES': {
        'anon': '2/minute',
        'user': '10/minute'
}
```

To test if the throttling is working properly, go to the **`http://127.0.0.1:8000/api/menu-items`** endpoint three times. After the second visit, the client will see an error message.

![Untitled](API%20throttling%20for%20class-based%20views%200899e35e34774adab04cf52e237e7bc0/Untitled.png)

API users with a valid token will see the same message after 10 successful calls to this endpoint.

# ****Conditional throttling****

It’s very easy to implement conditional throttling in class-based views. With conditional throttling, you can throttle API endpoints only for the specific HTTP methods, like **GET** calls, or **POST** calls.

For example, you can have conditional throttling that throttles **POST** calls, but not **GET** calls. You can do this by overriding the **`get_throttles`** method. In a class-based view that extends a **ModelViewSet** class, the **POST** call is handled by **create** methods. Similarly, the **GET** call is handled by the **list** method. Add the following lines of code to implement conditional throttling in the **MenuItemsViewSet** class.

```python
class MenuItemsViewSet(viewsets.ModelViewSet):
    queryset = MenuItem.objects.all()
    serializer_class = MenuItemSerializer
 
    def get_throttles(self):
        if self.action == 'create':
            throttle_classes = [UserRateThrottle]
        else:
            throttle_classes = []  
        return [throttle() for throttle in throttle_classes]
```

**Note**: *The* **throttle_classes** *is not used as a public attribute this time, which means the following line from the previous code example was removed.*

```python
throttle_classes = [AnonRateThrottle, UserRateThrottle]
```

Instead, this checks if the router called the **create** action, which handles the **POST** request. If that action is called, implement the throttling class **UserRateThrottle**. The **POST** calls will be limited to 10 calls per minute to this **`menu-items`** endpoint.

# ****Custom throttling classes****

You can use the custom throttling classes you created earlier in the course, like **TenCallsPerMinute** in the **throttles.py** file. All you have to do is import this class and then add it in the **throttle_classes** attribute, and you are done.

```python
from .throttles import TenCallsPerMinute
```

And then

```python
throttle_classes = [TenCallsPerMinute]
```

# ****Real world examples of API rate limits****

Here are some popular services and their current rate limit. This can help you to get some idea of how others are using such features in their API projects.

| Service | Anonymous | Authenticated |
| --- | --- | --- |
| Facebook graph API | X | 200/hour |
| Instagram API | X | 200/hour |
| Instagram messenger API | X | 100/second |
| WhatsApp messaging API | X | 80/second |

# **Conclusion**

In this reading, you learned how to implement throttling in class-based views and also how to create conditional throttling.