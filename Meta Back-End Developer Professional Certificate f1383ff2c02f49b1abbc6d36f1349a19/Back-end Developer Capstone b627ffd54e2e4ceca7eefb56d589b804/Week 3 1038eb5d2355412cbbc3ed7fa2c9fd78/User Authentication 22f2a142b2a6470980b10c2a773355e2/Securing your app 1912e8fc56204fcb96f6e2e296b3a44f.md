# Securing your app

Security is crucial when building any type of app, and it's important to protect your app's users from potential threats. One important aspect of security is making sure that unauthenticated users are not able to use the app. 

In this guide, we will go over the process of securing your app in Django.

# ****Session-Based Authentication****

**Django's authentication system is session-based,** and it uses middleware to authenticate requests. The Django Rest Framework (DRF) allows you to use different authentication schemes, such as remote user authentication, session authentication, and token-based authentication. Let's take a closer look at each of these.

# ****Basic Authentication****

The basic authentication scheme uses HTTP basic authentication, which is signed against a user's username and password. **Basic authentication is only appropriate for testing purposes.** If a user is successfully authenticated, the following credentials will be provided:

```python
Request.user = Django user instance
Request.auth = None
```

If a user is unauthenticated and their request is denied, an HTTP 401 unauthorized response will be returned.

# Session Authentication

The session authentication scheme uses Django's default session backend for authentication. It is appropriate for AJAX clients that are running in the same session context as your website.

# Token Authentication

Token authentication is appropriate for client-server setups, such as native desktop and mobile clients. To use token authentication, you need to add **`rest_framework.authtoken`** to the **`INSTALLED_APPS`** list in your **`settings.py`** file and run the migrate command. This will create the necessary table structure to hold the generated tokens.

```python
# settings.py
INSTALLED_APPS = [
    # ...
    'rest_framework.authtoken',
    # ...
]

# Run migrate command to create necessary table structure
python manage.py migrate
```

A token is a string of random alphanumeric characters, and you can generate a token for any user through the Django admin panel or programmatically. To secure a view, you can use the **`permission_classes`** decorator and set the **`is_authenticated`** attribute in the **`permissions`** model.

In your **`settings.py`** file, go to the DRF configuration section and set token authentication as the default authentication class. 

```python
# permissions.py
from rest_framework import permissions

class IsAuthenticated(permissions.BasePermission):
    def has_permission(self, request, view):
        return request.user and request.user.is_authenticated

# settings.py
REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': [
        'path.to.permissions.IsAuthenticated',
    ],
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework.authentication.TokenAuthentication',
    ],
}

# urls.py
from rest_framework.authtoken import views

urlpatterns = [
    # ...
    path('api/token/', views.obtain_auth_token, name='obtain-token'),
    # ...
]
```

To generate a token from an API endpoint, import the **`authtoken`** module in your **`urls.py`** file and set the root for the **`obtain_auth_token`** view. 

To get a token, send a POST request from a HTTP client such as Postman or Insomnia to the auth token endpoint, providing a username and password. The response will include the token, which can then be used to make HTTP calls to protected URLs.

Getting a Token:

```python
# Example using curl
curl -X POST -d "username=<user>&password=<password>" http://localhost:8000/api/token/

# Response
{
    "token": "936f1f77bcf86cd799439011c04f00e08e23fc48"
}
```