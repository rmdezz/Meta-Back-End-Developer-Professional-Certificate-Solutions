# Exercise: Set up the table booking API

# ****Overview****

So far, you have built a Menu API in the Restaurant app of your Django project with the name **LittleLemon**.

In this exercise, you will add a Table booking API in the restaurant app. The booking model is already declared and migrated.

# ****Scenario****

While building the table booking API, you will define a class-based view with Django REST Framework's **`ModelViewSet`** class. Declare the view class as **`BookingViewSet`**.

You will also use the **`DefaultRouter`** class to register the URL routes.

# Steps

## Step 1

Open the project in VS Code. Ensure that **`'rest_framework'`** is added in the **`INSTALLED_APPS`** list.

## Step 2

In the **`serializers.py`** file present in the app folder, declare the **`BookingSerializer`** class. Use the **`ModelSerializer`** as its base. Set the model attribute to `booking`, and fields to **`__all__**.`

```python
class BookingSerializer(ModelSerializer):
    class Meta:
        model = Booking
        fields = '__all__'
```

## Step 3

In the app's views module, declare the **`BookingViewSet`** class, inheriting the **`rest_framework.viewsets.ModelViewSet`** class.

Fetch all the objects from the **`booking`** model. Set the **`serializer_class`** attribute to **`BookingSerializer`**.

```python
from rest_framework import viewsets
from .models import Booking
from .serializers import BookingSerializer

class BookingViewSet(viewsets.ModelViewSet):
    queryset = Booking.objects.all()
    serializer_class = BookingSerializer
```

## Step 4

Open the **`urls.py`** file in the **`LittleLemon`** project package (not the restaurant app package folder).

Import the **`rest_framework.routers.DefaultRouter`** class. Call its register method to wire up the **`'booking'`** URL route with the **`BookingViewSet`** class.

```python
router.register(r'tables', views.BookingViewSet)
```

Add this router in the project's URL patterns.

```python
urlpatterns = [
path('restaurant/booking/', include(router.urls)),
]
```

```python
from django.contrib import admin
from django.urls import path, include
from rest_framework.routers import DefaultRouter
from restaurant.views import BookingViewSet

router = DefaultRouter()
router.register(r'tables', BookingViewSet)

urlpatterns = [
    path("admin/", admin.site.urls),
    path("restaurant/", include('restaurant.urls')),
    path("restaurant/booking/", include(router.urls)),
]
```

## Step 5

Visit the browsable API URL **`http://localhost:8000/restaurant/booking/tables`**. You can perform table booking operations in the browser window.

![Screenshot 2023-02-09 at 11.33.36 PM.png](Exercise%20Set%20up%20the%20table%20booking%20API%20f99910ab60ed4efea1385b42cecb7d81/Screenshot_2023-02-09_at_11.33.36_PM.png)

# Conclusion

In this exercise session, you built a table booking API with Django REST Framework.