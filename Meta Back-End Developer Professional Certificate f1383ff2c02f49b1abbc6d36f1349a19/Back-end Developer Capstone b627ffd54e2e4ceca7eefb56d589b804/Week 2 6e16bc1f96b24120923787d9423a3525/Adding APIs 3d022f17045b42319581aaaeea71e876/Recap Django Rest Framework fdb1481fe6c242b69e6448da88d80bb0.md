# Recap: Django Rest Framework

Django is a great Python framework for building web applications.

One of its most important features is its templating system, with which the web application renders an HTML response.

**Recall that an API returns a JSON or XML response to any client that consumes it.**

However, **the core Django framework is not suitable for this purpose.**

The Django REST Framework (DRF) acts as a wrapper around the core Django library. It serializes the view response into JSON format and returns it to the client.

### Serialization

Recall that the process of serialization involves converting the model instances to native Python datatypes so that they can be rendered into JSON format.

### Deserialization

Deserialization parses the data back into the model instance after first validating the incoming data.

### ModelSerializer

DRF provides a **ModelSerializer** class which provides a useful shortcut for creating serializers that deal with model instances and querysets.

To build a REST API with Django, you need to install the Django REST Framework in the same environment in which Django core is already present.

You can install the Django REST Framework with the following command:

```jsx
pip3 install djangorestframework
```

# First steps

Let us quickly recap the steps to create a Django project and an app:

```jsx
(workspace) C:\workspace>django-admin startproject demoproject . 
(workspace) C:\workspace>cd demoproject 
(workspace) C:\workspace>django-admin startapp demoapp 
(workspace) C:\workspace>cd.. 
(workspace) C:\workspace>python manage.py migrate 
(workspace) C:\workspace>python manage.py createsuperuser 
(workspace) C:\workspace>python manage.py runserver
```

The steps from the code snippet above create a Django project called **Demoproject** and, inside it, an app called **Demoapp**.

They also build the database structure for the pre-installed apps, create a super user, and run the server.

Once you create the superuser, you can log into the Django administration interface using those credentials.

Next, make sure that you update the **`INSTALLED_APPS`** list by adding **`'rest_framework'`** to it inside the **`settings.py`** file.

```jsx
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```

# Serializer class

The next step is to build a **`RESTful API`** to work with the **`User`** model defined in the pre-installed **`django.contrib.auth`** app. First, you declare a **`UserSerializer`** class to serialze the `**User**` model instance.

```jsx
from django.contrib.auth.models import User
from rest_framework import serializers
class UserSerializer(serializers.ModelSerializer):
    class Meta:
        model = User
        fields = ['url', 'username', 'email', 'groups']
```

Use the **`ModelSerializer`** as the base for the class. You need to set the model attribute of its Meta subclass to User and specify the fields to be exposed via the API.

# ****Views****

Next, we define the views for our app. DRF views can be of any of the following types:

- function-based views
- class-based views
- mixins
- generic view classes
- viewsets

## ****Viewset class****

Open the views.py file in the **`demoapp`** package folder and **`UserViewSet`** class.

The **`permission_classes`** attribute in the **ViewSet** class is set to the **`IsAuthenticated`** class. This makes the unauthentictated user unable to access this view.

The Django REST Framework supports function based views too. You must provide separate views for each method such as GET, POST, PUT and DELETE. Views based on generic ViewSets are concise. It makes the logic more organized.

To refresh your understanding, please visit the following link:

[Generic views and ViewSets in DRF](https://www.coursera.org/learn/apis/supplement/AlxEs/generic-views-and-viewsets-in-drf)

# URL Configuration

To wire up the API URLs, you can use the **DefaultRouter** class instead of declaring URL routes in the app and then including it in the project's **`URLConf`**.

```jsx
router = routers.DefaultRouter()  
router.register(r'users', views.UserViewSet)  

urlpatterns = [  

    path('', include(router.urls)),  
    path('api-auth/', include('rest_framework.urls', namespace='rest_framework'))
```

The **api-auth** route is defined to let you use the browsable API feature of DRF.

# Browsable API

Now that the code is ready, you can run the server if it is not already running and visit the URL for browsable API in the browser.

![Untitled](Recap%20Django%20Rest%20Framework%20fdb1481fe6c242b69e6448da88d80bb0/Untitled.png)

You can test the API from inside the browser itself and notice that the superuser you created in the beginning displays.

As an additional task, try and use the POST window to create another user.

In this Reading, you learned how to develop a basic API using the Django REST Framework.