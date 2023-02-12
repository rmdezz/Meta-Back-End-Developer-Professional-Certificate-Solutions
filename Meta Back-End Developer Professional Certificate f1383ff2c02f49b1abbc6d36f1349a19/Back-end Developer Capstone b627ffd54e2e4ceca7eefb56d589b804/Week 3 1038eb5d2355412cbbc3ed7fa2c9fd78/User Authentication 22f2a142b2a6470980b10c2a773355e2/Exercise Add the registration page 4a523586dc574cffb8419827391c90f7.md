# Exercise: Add the registration page

# Overview

So far, you have built the **`Menu API`** and **`Table booking API`** in your app.

In this exercise, you will add the feature of registering a new user in your Django project.

# ****Scenario****

The objective of this exercise is to be able to add a new user, and modify the existing user's credentials from within the app instead of the admin interface.

You will use the **Djoser** authentication library. Using the views defined in this library, you can easily implement registration, login and logout actions.

# ****Steps****

## **Step 1**

Install the **`djoser`** library in the current Django environment with PIP.

<aside>
🤔 **Note:** You should already have Django REST framework installed.

</aside>

## **Step 2**

Add the code **`'djoser'`** to the **`INSTALLED_APPS`** list in the **`settings.py`** file. Ensure that it is placed after the **`'rest_framework'`** app in the list.

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
    **"djoser",**
]
```

## Step 3

Add a new section in the **`settings.py`** file to set the **`DJOSER`** variable.

```python
#add the following line
DJOSER={"USER_ID_FIELD":"username"}
```

## **Step 4**

Make sure that the **TokenAuthentication** and **SessionAuthentication** classes are added to the **DEFAULT_AUTHENTICATION_CLASSES** section in the **REST_FRAMEWORK** setting.

```python
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework.authentication.TokenAuthentication',
        'rest_framework.authentication.SessionAuthentication',
    ]
}
```

## Step 5

Enable **djoser** endpoints by adding the following URL routes in the project's URL patterns.

```python
#add following lines to update urlpatterns list
path('auth/', include('djoser.urls')),
path('auth/', include('djoser.urls.authtoken'))
```

## Step 6

Run the migrations. Start the server and Login to the admin site with the superuser username and password. You should notice the **`Tokens`** section on the dashboard.

![Screenshot 2023-02-10 at 9.19.37 AM.png](Exercise%20Add%20the%20registration%20page%204a523586dc574cffb8419827391c90f7/Screenshot_2023-02-10_at_9.19.37_AM.png)

## **Step 7**

Visit the **Browsable API URL User List** – Django REST framework to get the list of users already registered.

```python
http://127.0.0.1:8000/auth/users/
```

![Screenshot 2023-02-10 at 9.20.55 AM.png](Exercise%20Add%20the%20registration%20page%204a523586dc574cffb8419827391c90f7/Screenshot_2023-02-10_at_9.20.55_AM.png)

## **Step 8**

Next you must register new user. ****To add a new user, use the form and submit a POST request.

```python
email: test@littlelemon.com
username: testuser
password: test@123!
```

![Screenshot 2023-02-10 at 9.21.52 AM.png](Exercise%20Add%20the%20registration%20page%204a523586dc574cffb8419827391c90f7/Screenshot_2023-02-10_at_9.21.52_AM.png)

## **Step 9**

To login, visit the **`djoser`** generated URL **http://127.0.0.1:8000/auth/token/login/**.

Enter the username and password to obtain the token.

![Untitled](Exercise%20Add%20the%20registration%20page%204a523586dc574cffb8419827391c90f7/Untitled.png)

![Screenshot 2023-02-10 at 9.22.19 AM.png](Exercise%20Add%20the%20registration%20page%204a523586dc574cffb8419827391c90f7/Screenshot_2023-02-10_at_9.22.19_AM.png)

## **Step 10**

To Logout, enter the URL **http://127.0.0.1:8000/auth/token/logout/**  with a POST method to logout the user.

![Screenshot 2023-02-10 at 9.22.57 AM.png](Exercise%20Add%20the%20registration%20page%204a523586dc574cffb8419827391c90f7/Screenshot_2023-02-10_at_9.22.57_AM.png)

![Screenshot 2023-02-10 at 9.23.32 AM.png](Exercise%20Add%20the%20registration%20page%204a523586dc574cffb8419827391c90f7/Screenshot_2023-02-10_at_9.23.32_AM.png)

# Conclusion

In this exercise, you used the **`djoser`** library to implement registration, login, and logout features.