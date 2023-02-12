# Token-based authentication in DRF

# Introduction

APIs are a great way to access your back-end data, but they also come with the risk of data breaches and corruption. Some APIs are open to the public, while others that modify data should only be accessible by authenticated clients. In this section, you will learn about the different types of authentication and how to implement them using Django Rest Framework (DRF).

# Password-Based Authentication

In password-based authentication, the client sends their username and password with every API call. The server verifies these credentials and delivers the appropriate response. However, this method is frustrating for the client and not very secure.

# Token-Based Authentication

Token-based authentication is the most popular method for API authentication. 

In this approach, the client sends their username and password once. If the credentials are valid, the server generates a unique piece of string, known as a token. This token is long, hard to read, and contains alphanumeric characters and symbols. The server can decide for how long the token will be valid, and when it expires. 

The client sends new API requests and includes the token in the header. The server-side scripts check if the token is valid, and if it has expired. They also find which user the token belongs to. This token is validated with the help of the **`TokenAuthentication`** class in the **`authtoken`** app provided by DRF. If everything is okay, the API will run on behalf of the user.

Here is an example of how to implement token-based authentication in DRF:

1.  Add **`rest_framework.authtoken`** to your installed app section in **`settings.py`**

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "rest_framework",
    **"rest_framework.authtoken", #here**
    "LittleLemonAPI",
]
```

1.  Run the necessary migrations from the **`authtoken`** app

```python
python3 manage.py makemigrations
python3 manage.py migrate
```

1. Create an admin user to access the Django admin panel using the command **`python manage.py createsuperuser`**
2. Access the admin panel from the local host **`http://localhost/admin`** and log in as the admin
3. In the Django admin panel, all previously created tokens for all users are displayed. You can also create tokens for new users here.
    
    ![Screenshot 2023-02-02 at 8.36.54 PM.png](Token-based%20authentication%20in%20DRF%2070921fbd1ba54dfb8855edb3c7209b6d/Screenshot_2023-02-02_at_8.36.54_PM.png)
    
4. In **`views.py`**, add the following code:
    
    ```python
    from rest_framework.decorators import api_view, permission_classes
    from rest_framework.permissions import IsAuthenticated
    
    @api_view()
    @permission_classes([IsAuthenticated])
    def secret(request):
        return Response({'message': 'Some secret message'})
    ```
    
5. Map this view to the **`/api/secret`** endpoint
    
    ```python
    urlpatterns = [
        path('menu-items', views.menu_items),
        path('menu-items/<int:id>', views.single_item),
        path('category/<int:pk>', views.category_detail, name = 'category-detail'),
        path('menu/', views.menu),
        **path('secret', views.secret), # here**
        path('api-token-auth/', obtain_auth_token),
    ]
    ```
    
6. Set **`TokenAuthentication`** as the default authentication class in the **`settings.py`** file
    
    ```python
    REST_FRAMEWORK = {
        'DEFAULT_RENDERER_CLASSES': [
            'rest_framework.renderers.JSONRenderer',
            'rest_framework.renderers.BrowsableAPIRenderer',
            'rest_framework_xml.renderers.XMLRenderer',
        ],
        'DEFAULT_AUTHENTICATION_CLASSES': (
            **'rest_framework.authentication.TokenAuthentication', # here**
        ),
    }
    ```
    
7. Copy the token from the Django admin panel
    
    ![Screenshot 2023-02-02 at 8.39.05 PM.png](Token-based%20authentication%20in%20DRF%2070921fbd1ba54dfb8855edb3c7209b6d/Screenshot_2023-02-02_at_8.39.05_PM.png)
    
8. Use the token in your API call by adding it to the header as **`Authorization: Bearer <token>`**
    
    ![Screenshot 2023-02-02 at 8.40.48 PM.png](Token-based%20authentication%20in%20DRF%2070921fbd1ba54dfb8855edb3c7209b6d/Screenshot_2023-02-02_at_8.40.48_PM.png)
    

# Generating Tokens from an API Endpoint

DRF also makes it easy to generate tokens from an API endpoint. Here's how:

1. In the **`urls.py`** file of your app, import the **`obtain_auth_token`** class from the **`rest_framework.token.views`** module
    
    ```python
    from rest_framework.authtoken.views import obtain_auth_token
    ```
    
2. Add the following URL pattern for token generation:
    
    ```python
    urlpatterns = [
        path('menu-items', views.menu_items),
        path('menu-items/<int:id>', views.single_item),
        path('category/<int:pk>', views.category_detail, name = 'category-detail'),
        path('menu/', views.menu),
        path('secret', views.secret),
        **path('api-token-auth/', obtain_auth_token), #here**
    ]
    ```
    
3. This endpoint only accepts HTTP POST calls, use a Form URL Encoded and write your username and password of your user as below:

![Screenshot 2023-02-02 at 8.39.45 PM.png](Token-based%20authentication%20in%20DRF%2070921fbd1ba54dfb8855edb3c7209b6d/Screenshot_2023-02-02_at_8.39.45_PM.png)