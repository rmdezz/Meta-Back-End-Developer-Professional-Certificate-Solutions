# Exercise: Securing the table booking API

# ****Overview****

In earlier exercises you already have the table booking API in the **`Restaurant`** app of your Django project with the name **`LittleLemon`**.

In this exercise, you will add token-based authentication to secure the Table booking API.

# Scenario

When you enable token authentication feature in the app, a random hexadecimal string that is unique for each user can be generated from inside the admin panel as well as from within the app.

**The HTTP client passes this token in the request header.** You can then restrict a view only for authenticated users.

# Steps

## Step 1

Add the **`'rest_framework.authtoken'`** app to the list of **`INSTALLED_APPS`** in the **`settings.py`** file

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "restaurant",
    "rest_framework",
    **"rest_framework.authtoken",**
]
```

## Step 2

Import the **`IsAuthenticated`** class from the **`rest_framework.permissions`** module in the **`views.py`** file.

```python
from rest_framework.permissions import IsAuthenticated
```

## **Step 3**

You already have the **`BookingViewSet`** class in the **views.py** file. To secure this view, set the permission_classes property to a list containing **`IsAuthenticated`**.

```python
permission_classes = [IsAuthenticated]
```

```python
class BookingViewSet(viewsets.ModelViewSet):
    permission_classes = [IsAuthenticated]
    queryset = Booking.objects.all()
    serializer_class = BookingSerializer
```

## Step 4

Open the app's **urls.py** and import the following function:

```python
#import obtain_auth_token view
from rest_framework.authtoken.views import obtain_auth_token
```

In the same file add a new URL route to the **urlpatterns** list:

```python
#add following line in urlpatterns list
path('api-token-auth/', obtain_auth_token)
```

```python
from django.urls import path
from . import views
from rest_framework.authtoken.views import obtain_auth_token

urlpatterns = [
    path('', views.index, name='index'),
    path('menu/', views.MenuItemsView.as_view()),
    path('menu/<int:pk>', views.SingleMenuItemView.as_view()),
    path('api-token-auth/', obtain_auth_token),
]
```

## **Step 5**

Run the server and visit the URL path **api-token-auth/** from the Insomnia client. You should select the POST method, and enter username and password in the body. When submitted, you get the token string as the response.

![Screenshot 2023-02-10 at 9.41.35 AM.png](Exercise%20Securing%20the%20table%20booking%20API%20ac83deb0e2c4434aa5812bdcaa85072a/Screenshot_2023-02-10_at_9.41.35_AM.png)

![Screenshot 2023-02-10 at 9.41.56 AM.png](Exercise%20Securing%20the%20table%20booking%20API%20ac83deb0e2c4434aa5812bdcaa85072a/Screenshot_2023-02-10_at_9.41.56_AM.png)

## Step 6

To get the response from a secured URL, select the **Auth** tab in Insomnia, choose the **Bearer** token from the drop down, and enter the token generated in the previous step and then press the send button.

![Screenshot 2023-02-10 at 9.44.44 AM.png](Exercise%20Securing%20the%20table%20booking%20API%20ac83deb0e2c4434aa5812bdcaa85072a/Screenshot_2023-02-10_at_9.44.44_AM.png)

![Screenshot 2023-02-10 at 9.45.27 AM.png](Exercise%20Securing%20the%20table%20booking%20API%20ac83deb0e2c4434aa5812bdcaa85072a/Screenshot_2023-02-10_at_9.45.27_AM.png)

![Screenshot 2023-02-10 at 9.45.42 AM.png](Exercise%20Securing%20the%20table%20booking%20API%20ac83deb0e2c4434aa5812bdcaa85072a/Screenshot_2023-02-10_at_9.45.42_AM.png)

![Screenshot 2023-02-10 at 9.45.52 AM.png](Exercise%20Securing%20the%20table%20booking%20API%20ac83deb0e2c4434aa5812bdcaa85072a/Screenshot_2023-02-10_at_9.45.52_AM.png)

# Conclusion

In this exercise, you implemented the **TokenAutentication** feature of Django REST framework to secure table booking API.