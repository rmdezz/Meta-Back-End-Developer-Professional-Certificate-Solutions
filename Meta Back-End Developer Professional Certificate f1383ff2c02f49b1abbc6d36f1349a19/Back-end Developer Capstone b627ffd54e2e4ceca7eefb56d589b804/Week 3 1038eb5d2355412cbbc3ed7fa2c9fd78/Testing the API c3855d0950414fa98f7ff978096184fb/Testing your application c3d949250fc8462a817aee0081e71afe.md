# Testing your application

# Introduction

Testing is a crucial part of the software development process that helps validate that your code works as expected. When working with an existing codebase, tests can ensure that changes you make don't negatively impact the application's behavior. Testing a web application can be challenging as it involves multiple layers such as request handling, form validation and processing, and template rendering.

# Testing a Django RESTFUL API

In this guide, we'll be exploring the steps involved in testing a Django RESTful API using the unit test framework. We'll be working with a Django project named **`Littlelemon`** and an app within the project named **`LittlelemonAPI`**.

# Installing Django REST Framework

First, install the Django REST framework in the current Python environment. Start a Django project and create an app named **`LittlelemonAPI`** within the project. Add the app to the **`INSTALLED_APPS`** in the **`settings.py`** file.

# Creating a model

Next, create a model named **`MenuItem`** and run the migrations. Create an admin superuser and log into the Django administration interface. Populate the **`MenuItem`** table with some data.

# ****Serialization and Views****

Open the **`serializers.py`** file and create the necessary serialization code. Create the views for the **`MenuItem`** and **`SingleItem`**.

# ****URL Routing****

Create the appropriate URL routing in the **`urls.py`** file of the app. Make sure to include the URL patterns of the app in the **`urls.py`** file of the project.

# ****Launching the Development Server****

Once the code is set up, run the command to launch the development server. The Django REST framework provides a browsable API that generates HTML output for different resources. You can interact with the RESTful web service through any web browser.

# ****Browsable API and Insomnia REST Client****

Open a browser at the default localhost URL and add **`/api/menu-items/`** to the URL. An interface will load and you can send HTTP requests through it. You can also use the Insomnia REST client to interact with the API and test the routes.

**Example:**

```python
GET /api/menu-items/
```

```python
HTTP 200 OK
Allow: GET, POST, HEAD, OPTIONS
Content-Type: application/json
Vary: Accept

[
    {
        "id": 1,
        "name": "Cheese Pizza",
        "description": "A delicious cheese pizza",
        "price": 10.99
    },
    {
        "id": 2,
        "name": "Pepperoni Pizza",
        "description": "A delicious pepperoni pizza",
        "price": 12.99
    }
]
```

# ****Unit Tests****

Create a **`test`** folder inside the **`Littlelemon`** package folder and create a file named **`test_models.py`**. Add the model test code and save the file. Run the test command to perform the test. The console will display the test result and confirm that the test ran successfully.

**Example:**

```python
python manage.py test
```

```python
Ran 1 test in 0.001s

OK
```

# Conclusion

In this guide, you learned how to test a Django RESTful API using the browsable API, Insomnia REST client, and unit tests.