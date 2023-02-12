# Recap: User Authentication

# Introduction

When a REST API exposes the back-end models to the external world, **the access needs to be authenticated.**

Django framework provides a basic session-based authentication. Certain middleware components are needed for Django's auth backends authenticate requests.

Django REST Framework presents different other authentication schemes other than session-based authentication.

**Token-based authentication is the most suited one when the web application interacts with desktop and mobile clients.**

# Prerequisites

A Python virtual environment is set up with Django as well as Django REST Framework installed in it.

A Django project with the name LittleLemon is created. Inside it, a Django app with LittleLemonAPI its name is also present.

# ****Enable Token Authentication****

Add **'rest_framework'**, **'LittleLemonAPI'**, and **'rest_framework.authtoken'** in the project's **settings.py** file

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
    "rest_framework.authtoken",
]
```

Add **`'rest_framework.authentication.TokenAuthentication'`** to the **`AUTHENTICATION_CLASSES`** list:

```python
REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.IsAuthenticated',
    ],
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework.authentication.TokenAuthentication',
    ],
}
```

 and run the migrate command **to create the necessary database tables for storing the generated tokens:**

```python
python manage.py migrate
```

With these changes, token based authentication will be enabled for your Django REST Framework app.

Visit the admin panel with [http://localhost:8000/admin](http://localhost:8000/admin) URL and log in with superuser credentials.

The site administration dashboard shows the **AUTH TOKEN** section.

![Screenshot 2023-02-10 at 12.54.03 AM.png](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Screenshot_2023-02-10_at_12.54.03_AM.png)

# ****Model****

Open the VS Code editor, and ensure that the **`LittleLemonAPI`** app contains the definition of the **`MenuItem`** model in the **models.py** file.

```python
from django.db import models

# Create your models here.
class MenuItem(models.Model):
    title = models.CharField(max_length=255)
    price = models.DecimalField(max_digits=6, decimal_places=2)
    inventory = models.SmallIntegerField()

    def get_item(self):
        return f'{self.title} : {str(self.price)}'
```

Run the commands **makemigrations** and **migrate** to create the table structure.

To refresh your understanding of models and migrations, refer to these links:

- [Django Web Framework - Video: Creating models](https://www.coursera.org/learn/django-web-framework/lecture/yAFex/creating-models)
- [Django Web Framework - Video: Migrations](https://www.coursera.org/learn/django-web-framework/lecture/tMqae/migrations)
- [Django Web Framework - Reading: How to use migrations](https://www.coursera.org/learn/django-web-framework/supplement/wcsZg/how-to-use-migrations)
- [Django Web Framework - Video: Working with migrations](https://www.coursera.org/learn/django-web-framework/lecture/V0P1d/working-with-migrations)

# Serializers

The Django REST API needs a **`serializer`** class to convert the model instances into JSON format. Add a new module **`serializers.py`** in the app folder and declare the **`MenuItemSerializer`** class subclassing **`ModelSerializer`**.

```python
from rest_framework.serializers import Serializer
from .models import MenuItem

class MenuItemSerializer(Serializer):
    class Meta:
        model = MenuItem
        fields = '__all__'
```

# Views

To create the views you must subclass the **`ListCreateView`** that handles the HTTP GET and POST operations.

Similarly add a **`SingleMenuItemView`** class for PUT, GET and DELETE methods.

```python
class MenuListView(generics.ListCreateAPIView):
    queryset = MenuItem.objects.all()
    serializer_class = MenuItemSerializer
    
class SingleMenuItemView(generics.RetrieveUpdateDestroyAPIView):
    queryset = MenuItem.objects.all()
    serializer_class = MenuItemSerializer
```

To recap different type of views in DRF follow these links:

- [APIs course - Video: Function and class-based Views](https://www.coursera.org/learn/apis/lecture/4BASB/function-and-class-based-views)
- [APIs course - Reading: Different types of routing in DRF](https://www.coursera.org/learn/apis/supplement/cFRCv/different-types-of-routing-in-drf)
- [APIs course - Reading: Generic views and ViewSets in DRF](https://www.coursera.org/learn/apis/supplement/AlxEs/generic-views-and-viewsets-in-drf)

# URLs

Declare the URL routes of the app.

```python
from django.urls import path
from . import views

urlpatterns = [
    path('menu-items/', views.MenuItemsView.as_view()),
    path('menu-items/<int:pk>', views.SingleMenuItemView.as_view()),
]
```

Wire up the app's URLs with that of the project's URLConf.

```python
from django.contrib import admin
from django.urls import path, include
from LittleLemonAPI import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/',include('LittleLemonAPI.urls'))
]
```

# Authentication

Your API is now ready. Visit **`http://localhost:8000/api/menu-items**` to test the POST and GET operations.

Next is the authentication part. The views that were added need no authentication.

Now it's time to add a view that will need authentication.

This is done by mentioning **`@permission_classes([IsAuthenticated])`** decorator above the function-based view. The following view displays a protected message.

```python
#in views.py
from rest_framework.decorators import api_view, permission_classes
from rest_framework.permissions import IsAuthenticated

@api_view()
@permission_classes([IsAuthenticated])
# @authentication_classes([TokenAuthentication])
def msg(request):
    return Response({"message":"This view is protected"})
```

Don't forget to update the app's URL configuration with URL route of the msg() view

```python
urlpatterns = [
    path('menu-items/', views.MenuItemsView.as_view()),
    path('menu-items/<int:pk>', views.SingleMenuItemView.as_view()),
    path('message/', views.msg),
]
```

If you try to issue a GET request using the Insomnia client, you get the **'authentication credentials not provided'**. So, this view requires authentication.

![Untitled](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Untitled.png)

Now go back to the admin panel and **obtain the token** for admin user.

![Untitled](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Untitled%201.png)

Open the Insomnia app window and insert the token value to authenticate the request.

![Screenshot 2023-02-10 at 8.54.13 AM.png](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Screenshot_2023-02-10_at_8.54.13_AM.png)

The **/api/message/** route now shows the desired response.

You can also obtain the token by visiting the following URL: **/api/'api-token-auth/**

Add this route in the app's urls.py file.

```python
from django.urls import path
from rest_framework import routers
from . import views
from rest_framework.authtoken.views import obtain_auth_token

urlpatterns = [
    path('menu-items/', views.MenuItemsView.as_view()),
    path('menu-items/<int:pk>', views.SingleMenuItemView.as_view()),
    path('message/', views.msg),
    path('api-token-auth/', obtain_auth_token)
]
```

Go to the Insomnia app and visit this URL. Enter username and password in the body.

![Untitled](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Untitled%202.png)

![Screenshot 2023-02-10 at 8.57.43 AM.png](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Screenshot_2023-02-10_at_8.57.43_AM.png)

You can also enforce authentication to the model view by adding the **`IsAuthenticated`** requirement in the view class.

```python
class MenuItemsView(generics.ListCreateAPIView):
  permission_classes = [IsAuthenticated]
  queryset = MenuItem.objects.all()
  serializer_class = MenuItemSerializer
```

The list of menu items will be displayed in the response window only after entering the token.

![Screenshot 2023-02-10 at 8.59.21 AM.png](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Screenshot_2023-02-10_at_8.59.21_AM.png)

![Screenshot 2023-02-10 at 8.59.51 AM.png](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Screenshot_2023-02-10_at_8.59.51_AM.png)

![Untitled](Recap%20User%20Authentication%2038d8d37d2cdf490a9ccb2ba137e98c2e/Untitled%203.png)

# Conclusion

In this Reading, you learned to apply token authentication scheme to the LittleLemonAPI app.

You can revisit the concept of token-based authentication from the following link:

[APIS course - Video: Token based authentication in DRF](https://www.coursera.org/learn/apis/lecture/MJTLM/token-based-authentication-in-drf)