# MVT Overview

In this Reading, you will learn about Django's Model, View and Template (MVT) application development pattern.

# Web Framework

- A software framework is a standard, reusable software platform that facilitates the rapid development of software applications
- The web framework (also called web application framework) provides a generic functionality needed for building web applications, APIs and web services
- The main advantage of employing a web framework for development is that it provides "out of the box" support to perform everyday operations in the web development process
- **For example, it easily connects applications to databases and handles tasks such as session management**
- It also integrates with templating tools to render dynamic content on web pages

# MVC Architecture

- Most web frameworks implement the Model-View-Controller (MVC) architecture
- In the MVC approach, the controller intercepts user requests and coordinates with the view and model layers to send the appropriate response back to the client
- The model is responsible for data definitions, processing logic, and interaction with the backend database
- The view is the presentation layer and takes care of the placement and formatting of the result

![Untitled](MVT%20Overview%202284ef3654f944f680bdfced327e15b3/Untitled.png)

# MVT Architecture

- The **Django framework adapts a Model, View and Template (MVT) approach**, a slight variation of the MVC approach
- **The model is the data layer, the view is the processing logic layer, and the template is the presentation layer**
- A Django application consists of the following components: URL dispatcher, View, Model, and Template

![Untitled](MVT%20Overview%202284ef3654f944f680bdfced327e15b3/Untitled%201.png)

## URL Dispatcher

- Django's URL dispatcher mechanism is equivalent to the controller in the MVC architecture
- **The urls.py module in the Django project's package folder acts as the dispatcher and defines the URL patterns**
- Each URL pattern is mapped with a view function to be invoked when the client's request URL is found to be matching with it
- The URL patterns defined in each app under the project are also included.

Here’s the **urls.py** file in the app folder.

```python
from django.urls import path 
from . import views 

urlpatterns = [ 
    path('', views.index, name='index'), 
]
```

When the server receives a request in the client URL, the dispatcher matches its pattern with the patterns available in the **urls.py**.

It then routes the flow of the application toward its associated view.

### Analogy

The URL dispatcher can be thought of as a hall monitor or security guard for the building. It's responsible for making sure that visitors are going to the right room and not getting lost.

The URL dispatcher looks at the address that the visitor types into the browser, like **[www.example.com/about-us](http://www.example.com/about-us)**, and matches it to the right "room" or page on the website.

<aside>
🤔 Just like a hall monitor makes sure students are going to the right class and not sneaking into places they shouldn't be, the URL dispatcher makes sure visitors are being directed to the right page on the website and not trying to access something they shouldn't be able to.

</aside>

Also, when an user access the website the URL dispatcher checks if the entered URL is matching with the URL patterns defined in the urls.py file. If there's a match, it directs the flow of the application towards the correct view, otherwise it throws an error page.

## View

- The view function reads the path, query, and body parameters included in the client's request.
- If required, it uses this data to interact with the models to perform CRUD operations.
- A view can be a user-defined function or a class.
- You create View definitions in the **views.py**file of the respective app package folder.
- The following code in the **view.py** file defines the **index()** view function.

```python
from django.shortcuts import render 
# Create your views here. 
from django.http import HttpResponse 

def index(request): 
    return HttpResponse("Hello, world.")
```

### Analogy

The View is like the janitor of the building. It's responsible for taking care of the different rooms and making sure they are clean and ready for visitors. It also controls how the different rooms interact with each other and the outside world.

### Example

- For example, if a visitor wants to see a list of products on an e-commerce website, the view function would read the request from the visitor and then use that information to communicate with the model and retrieve a list of products from the database. It would then take that list of products and send it to the template for it to be displayed to the visitor.
- It's also responsible for handling any user input and performing any necessary actions such as adding a product to a shopping cart or sending a contact form.
- So the view is like the bridge that connects the outside world with the website's internal operations and data, it acts as a control center, receiving input, asking the model to perform actions **and passing data to the template to be presented to the client.**

## Model

Model refers to the data layer of the application. Think of a model as a blueprint or a template for creating an object or a "thing" in the real world.

> For example, in an e-commerce website, a model for a product would include things like the product's name, price, and description. This information is then used to create the actual product objects that the visitor can view and purchase.
> 
- In a Django application, a model is represented by a Python class in the models.py file. The class defines the attributes and properties of the "thing" you want to create, and Django uses these attributes to create a database table of the same structure.
- Django also provides an Object Relational Mapper (ORM) to perform CRUD operations on the data in an object-oriented way, instead of writing raw SQL queries. This allows the developer to interact with the database in a more intuitive way.

> For example, the view function may retrieve a list of products from the database by calling a model method and the ORM will handle the SQL query required to fetch the data, so the developer doesn't have to worry about the underlying database operations.
> 

**The view uses the model's data, in addition to the client's request data, to perform actions and render its response using a template, the final layer of the MVT.**

## Template

- The template is **the presentation layer of the MVT architecture, and it's responsible for how the final output looks like.**
- A template is a web page that contains a combination of static HTML and dynamic code blocks written in Django Template Language (DTL).

For example, imagine you are creating a template for a product page. The page's layout, such as headings, images, and buttons, would be written in HTML, while the specific product details, such as the product name and price, would be included using DTL code blocks.

In a Django application, you place the templates in a folder named "templates" with a .html file extension.

When the view receives a request, it uses the context data and calls the template. Django's template processor then fills in the DTL code blocks with the appropriate data, creating a dynamic response to be sent back to the user.

For example, the view function may pass a list of products to the template, and the DTL code will loop through the list, displaying each product's name and price.

# Conclusion

This MVT architecture provides a clear separation of concerns, making it easy to maintain and modify the web application. The model and view handle the logic and data processing, while the template handles the presentation and layout of the final output.