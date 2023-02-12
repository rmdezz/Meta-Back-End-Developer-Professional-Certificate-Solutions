# Introduction to Djoser library for better authentication

# Introduction to Djoser

- Authentication and authorization are crucial parts of every application
- Django and DRF can be tedious and time-consuming to do everything from scratch every time
- Djoser offers a simple authentication library to configure with just a few lines of code

# Installing Djoser

- Use Pipenv to install the Djoser package in your project
- Make sure you have activated your virtual environment using Pipenv shell
- Run the command **`pipenv install djoser`**

# Configuring Djoser

## **settings.py**

- Add the Djoser app in the installed app section after the rest_framework app
    
    ```python
    INSTALLED_APPS = [
        "django.contrib.admin",
        "django.contrib.auth",
        "django.contrib.contenttypes",
        "django.contrib.sessions",
        "django.contrib.messages",
        "django.contrib.staticfiles",
        "rest_framework",
        "rest_framework.authtoken",
        "LittleLemonAPI",
        **"djoser", #here**
    ]
    ```
    
- Create a section called **`DJOSER`** and add the **`user_id_field`** and **`username`**
    
    ```python
    DJOSER = {
        "USER_ID_FIELD": "username",
        #"LOGIN_FIELD": "email",
    }
    ```
    
- Add the **`TokenAuthentication`** class in the **`DEFAULT_AUTHENTICATION_CLASSES`**
- Add the **`SessionAuthentication`** class if you want to use the Django admin login
    
    ```python
    REST_FRAMEWORK = {
        'DEFAULT_RENDERER_CLASSES': [
            'rest_framework.renderers.JSONRenderer',
            'rest_framework.renderers.BrowsableAPIRenderer',
            'rest_framework_xml.renderers.XMLRenderer',
        ],
        'DEFAULT_AUTHENTICATION_CLASSES': (
            **'rest_framework.authentication.TokenAuthentication',**
            **'rest_framework.authentication.SessionAuthentication',**
        ),
    }
    ```
    

## URLs.py

- Enable the Djoser endpoints by adding these two lines in the **`urlpatterns`** section

```python
urlpatterns = [
    path("admin/", admin.site.urls),
    path("api/", include('LittleLemonAPI.urls')),
    **path("auth/", include('djoser.urls')), #this
    path("auth/", include('djoser.urls.authtoken')), #this**
]
```

# Djoser Endpoints

Djoser offers several handy endpoints. Some support only the **`GET`** method and some support **`POST`**, **`PUT`**, **`PATCH`**, and **`DELETE`** methods. You can access these endpoints by adding **`http://127.0.0.1:8000/auth`** in front of each one of them.

- The **`/auth/users`** endpoint lists all the users, and you can make a **`POST`** call to create a new one.
- The **`/auth/token/login`** endpoint allows you to create tokens for a user.
- The **`/auth/users/me`** endpoint provides the details of the authenticated user, and it supports a **`PUT`** call to update the email address of this user.

| Endpoints |
| --- |
| /users/ |
| /users/me/ |
| /users/confirm/ |
| /users/resend_activation |
| /users/set_password/ |
| /users/reset_password/ |
| /users/reset_password_confirm/ |
| /users/set_username/ |
| /users/reset_username/ |
| /users/reset_username_confirm/ |
| /token/login/ |
| /token/logout/ |

# Conclusion

With Djoser and a few lines of configuration, you get several handy API endpoints to deal with users and token-based authentication in your DRF project. 

In this video, you learned about Djoser, how to install and configure it correctly in your DRF API project, and the handy endpoints offered by the Djoser library.