# Registration and authentication endpoints with JWT

# Introduction

- JSON Web Token (JWT) is a popular token system for API authentication.
- In this video, you'll learn how to implement JWT in your DRF API project.

# Installing and configuring JWT

- To implement JWT based authentication, you need the **`djangorestframework-simplejwt`** package.
- Activate the virtual environment of your project using **`pipenv shell`** and run the command **`pipenv install djangorestframework-simplejwt ~= 5.2.1`**.
- Go to your **`settings.py`** file and add **`rest_framework_simplejwt`** in the installed apps section.
- In the **`settings.py`** file, add the JWT authentication classes to the default authentication class in the rest framework session.
    
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
        "djoser",
        "rest_framework_simplejwt",
    ]
    ```
    
- Input some essential classes from the rest framework, simple JWT views module.
    
    ```python
    from rest_framework_simplejwt.views import TokenObtainPairView, TokenRefreshView, TokenBlacklistView
    ```
    
- The simple JWT package needs API endpoints to receive the username and password and generate the JWT token. To enable those endpoints, open the main **`URLs.py`** file and add these two lines in the URL patterns array:
    
    ```python
    urlpatterns = [
        ...
        path("api/token/", TokenObtainPairView.as_view(), name = "token_obtain_pair"),
        path("api/token/refresh/", TokenRefreshView.as_view(), name = "token_refresh"),
    ]
    ```
    

# Creating a JWT Token

- Use a tool like insomnia to create a JWT token.
- Send the username and password in an HTTP post call to the endpoint
    
    ```python
    http://127.0.0.1:8000/api/token/
    ```
    
    ![Screenshot 2023-02-02 at 11.21.22 PM.png](Registration%20and%20authentication%20endpoints%20with%20JWT%201f1bd93fae1548b39c219cac909e2008/Screenshot_2023-02-02_at_11.21.22_PM.png)
    
- Two tokens are returned as a response: an access token and a refresh token.
    
    ```python
    Example:
    
    {
    	"refresh": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY3NTQ4Mjk3NCwiaWF0IjoxNjc1Mzk2NTc0LCJqdGkiOiJhNTI3NmJlYmUxNjE0YjA1YmNhZTJkZDVhNWNmMWE4MCIsInVzZXJfaWQiOjN9.uOHIICZfK_EhIMrj9jt0yNZr8bkx2xF5FZwjF-HBXhw",
    	"access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjc1Mzk2ODc0LCJpYXQiOjE2NzUzOTY1NzQsImp0aSI6IjI0Yzg5YzYxMmYwNjQ0M2I5YTQyNWU5ZjEyYWVkNTMwIiwidXNlcl9pZCI6M30.LuBY9AX4kiNwBEfyIWj6DIJJffVHxsBYhMXbkJO2OAk"
    }
    ```
    
- The client will use the access token to authenticate API calls. This access token expires after five minutes in simple JWT.
- **The refresh token is used to regenerate the access token when it expires.**
- You can specify the period after which the access token expires in the **`settings.py`** file, but it's always a good idea to keep this expiry short.
    
    ```python
    SIMPLE_JWT = {
        'ACCESS_TOKEN_LIFETIME': timedelta(minutes = 5),
    }
    ```
    
- To test the JWT authentication, copy the access token in insomnia, create a new HTTP request to the endpoint **`http://127.0.0.1:8000/api/secret`** and select "Bearer" in the "ALT" tab. Paste the access token in the token field and send the request.
    
    ![Screenshot 2023-02-02 at 11.23.30 PM.png](Registration%20and%20authentication%20endpoints%20with%20JWT%201f1bd93fae1548b39c219cac909e2008/Screenshot_2023-02-02_at_11.23.30_PM.png)
    

# Regenerating Access Tokens

- When the access token expires, the client can use the refresh token to regenerate a new access token.
- Create another HTTP post call in insomnia to the endpoint **`http://127.0.0.1:8000/api/token/refresh/`**. In the body tab, select "Form URL Encoded" and add "refresh" as the key and the previous refresh token as value.
    
    ![Screenshot 2023-02-02 at 11.24.14 PM.png](Registration%20and%20authentication%20endpoints%20with%20JWT%201f1bd93fae1548b39c219cac909e2008/Screenshot_2023-02-02_at_11.24.14_PM.png)
    
- A new access token will be generated, which the client can use to make authenticated API calls again.

# Blacklisting Tokens

To block a client from generating JWT access tokens, you can use a utility blacklisting app provided by the simplejwt package. This app will be used to blacklist the refresh token so it can no longer generate an access token.

- Add this line of code in the installed apps section in the **`settings.py`** file: **`restframework_simplejwt.token_blacklist`**
    
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
        "djoser",
        "rest_framework_simplejwt",
        **"rest_framework_simplejwt.token_blacklist", #this**
    ]
    ```
    
- To use the token blacklist app, run migrations. Stop the web server and run this command in the terminal: **`python manage.py migrate`**
- Re-run the web server.
- Open the main **`URLs.py`** file and import the **`TokenBlacklistView`** class from the **`rest_framework_simplejwt.views`** module.
    
    ```python
    from rest_framework_simplejwt.views import TokenBlacklistView
    ```
    
- Add the following code to the URL patterns path to enable this token blacklist API endpoint:
    
    ```python
    urlpatterns = [
        ...
        path("api/token/blacklist/", TokenBlacklistView.as_view(), name="token_blacklist"),
    ]
    ```
    
- Create a new HTTP POST request to the endpoint **`http://127.0.0.1:8000/api/token/blacklist/`**.
- Click on the Body tab and add **`refresh`** as the key and the previous refresh token as value.
- Send the request. DRF will return an empty response.
    
    ![Screenshot 2023-02-02 at 11.26.39 PM.png](Registration%20and%20authentication%20endpoints%20with%20JWT%201f1bd93fae1548b39c219cac909e2008/Screenshot_2023-02-02_at_11.26.39_PM.png)
    
- This refresh token has now been blacklisted.
- Try to regenerate the access token with this blacklisted refresh token. DRF will now tell you that this refresh token is blacklisted and can no longer be used.
    
    ![Screenshot 2023-02-02 at 11.26.55 PM.png](Registration%20and%20authentication%20endpoints%20with%20JWT%201f1bd93fae1548b39c219cac909e2008/Screenshot_2023-02-02_at_11.26.55_PM.png)
    

# Conclusion

And that's everything you need to know about using JWT tokens for API authentication in your DRF projects! You learned about JSON Web Token (JWT) and how to use JWT tokens to authenticate API calls. You also learned how to regenerate access tokens using a refresh token and blacklist a refresh token if needed. With this knowledge, you are one step closer to creating secure APIs. Well done!