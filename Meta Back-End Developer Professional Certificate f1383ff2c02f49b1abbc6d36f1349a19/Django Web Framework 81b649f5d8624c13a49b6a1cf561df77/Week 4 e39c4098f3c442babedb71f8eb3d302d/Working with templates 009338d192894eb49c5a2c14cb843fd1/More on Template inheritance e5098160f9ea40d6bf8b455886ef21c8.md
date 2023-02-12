# More on Template inheritance

This reading introduces template inheritance, along with its main features.

You will learn how template inheritance can be used inside a standard HTML page and how child templates can override blocks inside it. Additionally, you will explore the concept of static files in Django.

# Inheritance in Django Template Language

The term inheritance is associated with the principle of object-oriented programming. It refers to the mechanism of a child class inheriting the properties of its parent class, and if required, extending or overriding them.

The question is how is the term inheritance used in relation to the template language?

There are many view functions defined in a Django application. Each view renders a different template (or the same with a different context). Ideally, you want all the web pages to look consistent. For example, elements such as the header, footer, and the navigation bar, must appear similar across all pages.

# Structure of parent template

Let us assume that you’re building a three-page web application with a home page, a registration page, and another for logging into the application. 

Each page should have a main header, a footer, and a sidebar with links to the pages. The corresponding content of each page should appear to the right of the sidebar and between the header and footer.

![Untitled](More%20on%20Template%20inheritance%20e5098160f9ea40d6bf8b455886ef21c8/Untitled.png)

## {% block %} tag

Template inheritance helps to implement this structure and it’s similar to the one in object-oriented programming. It is a very powerful, yet equally complex feature of Django Template Language. Template inheritance is implemented with the **{% block %}** and **{% endblock %}** tags.

```lua
{% block name %} 
  ... 
{% endblock %}
```

The block is identified by the given name to be overridden in the child template.

First, identify the components that are required because these will be used across all the web pages. Include those that show variable content on each page. Use the block tags to mark the code blocks with variable content as a dummy block or with no contents.

## Base template

For the above skeletal structure, the header is represented by the following HTML:

```lua
<!--header-->   
<div style="height:10%;">   
<h2 align="center">Django Web Application</h2>   
<hr>   
</div>
```

The middle part of the page has two sections, represented in two **<div>** tags of 20% and 80% width. The one on the left is a sidebar.

```lua
<!—side bar-->   
<div style="width:20%; float:left; border-right-style:groove">   
<ul>   
<b>   
<li><a href="#">home</a></li>   
<li><a href="#">register</a></li>   
<li><a href="#">login</a></li>   
</b>   
</ul>   
</div>
```

For now, let us add dummy links to the menu items.

The remaining part of the page is where the contents of each page will be displayed. Once again, mark this as a dummy block with no text between the block tags.

```lua
<!--contents-->  
<div style="margin-left:21%;">  
<p>   
{% block contents %}  

{% endblock %} 
</p>  
</div>
```

Now, address the footer of the page.

```lua
<!--footer-->   
<hr>   

<div>   
<h4 align="right">All rights reserved</h4>   
</div>
```

Put the above code blocks in a **`base.html`** file and save it in the **`templates`** folder. Note that this file will never be rendered as is but the templates for **`home`**, **`register`,** and **`login` views** will inherit it.

## Add views

Now, add the view functions for the three operations planned for the applications. Open the **views.py** file and add the following code:

```lua
def home(request): 
    return render(request, "home.html", {}) 

def register(request): 
    return render(request, "register.html", {}) 

def login(request): 
    return render(request, "login.html", {})
```

You also need to update the URL pattern of the app.

```lua
urlpatterns = [  
		. . ., 
		. . ., 
    path('home/', views.home, name='home'), 
    path('register/', views.register, name='register'),  
    path('login/', views.login, name='login'),  
]
```

Next, replace the dummy hyperlinks in the sidebar with the URLs registered above.

```lua
<!—side bar--> 
<div style="width:20%; float:left; border-right-style:groove"> 

<ul> 
<b> 
<li><a href="/myapp/home/">home</a></li> 
<li><a href="/myapp/register/">register</a></li> 
<li><a href="/myapp/login/">login</a></li> 
</b> 
</ul> 
</div>
```

## Child templates

Writing the templates for the **`views`** is straightforward because the structure is already defined in the **`base.html`**. The **`{% extends %}`** tag imports the base template components in the child template. Create a new file named **`home.html`** in the **`templates`** folder and add the following line.

```lua
{% extends "base.html" %}
```

We intend to keep the same header, the sidebar, and the footer defined in the base template **and put the relevant code inside the contents block**. Now, add the following lines in **`home.html`** and save it.

```lua
{% block contents %} 
<h2 align="center">This is Home page</h2> 
{% endblock %}
```

At this stage, start the server and visit **/myapp/home/** URL. Since this path is mapped to the **`home()`** view, you should get the following page:

![Untitled](More%20on%20Template%20inheritance%20e5098160f9ea40d6bf8b455886ef21c8/Untitled%201.png)

Similarly, create **`register.html`**and put it in the templates folder.

```lua
{% extends "base.html" %} 

{% block contents %} 
<h2 align="center">Registration Form appears here</h2> 
{% endblock %}
```

The **/myapp/register/** URL invokes the **register()** function. It renders the registration page as below:

![Untitled](More%20on%20Template%20inheritance%20e5098160f9ea40d6bf8b455886ef21c8/Untitled%202.png)

Before creating the login page, let us make some changes to the base template. You’ll want the login page to display some additional text in the footer. For that, the footer is placed in the block tag. Open the **`base.html`** and change the footer to:

```lua
<!--footer-->   
<hr>   

{% block footer %}   
<div>   
<h4 align="right">All rights reserved</h4>   
</div>   
{% endblock %}
```

Now, save the **`login.html`** template with the following code:

```lua
{% extends "base.html" %} 

{% block contents %} 
<h2  align="center">Login Form appears here</h2> 
{% endblock %} 
{% block footer %} 
{{ block.super }} 
<h4 align="right">Designed By: Alexa Designs Ltd</h4> 
    {% endblock %}
```

Notice that the **{% block.super %}** tag has been used. **It is similar to Python’s super()function whereby you access the parent class methods in a child class.** In the same way, the contents of the footer block will be rendered on the login page. Now, include additional text in the block as a part of the header, for the login page.

So, we have a "**base.html**" and three child templates – "**home.html**", "**register.html**" and "**login.html**" - in the templates folder.

![Untitled](More%20on%20Template%20inheritance%20e5098160f9ea40d6bf8b455886ef21c8/Untitled%203.png)

The**/myapp/login/** URL displays the following output with the modified footer.

![Untitled](More%20on%20Template%20inheritance%20e5098160f9ea40d6bf8b455886ef21c8/Untitled%204.png)

## Static files

In addition to the dynamic content, a web application needs to serve certain static content to the client. It may be in the form of images, JavaScript code, or style sheets. Django’s default project template includes **django.contrib.staticfiles** in **INSTALLED_APPS**.

The project’s settings file `(**settings.py**)` has a **`static_url`** property set to **`'static/'`**. All the static assets must be placed in the **`myapp/static/myapp`** folder as the **`static_url`** refers to it.

While rendering an image from this static folder, load it with the **{% static %}** tag. HTML provides the **<imgsrc>** tag. Instead of giving the physical URL of the image to be rendered, use the path that is relative to the defined **`static_URL`**.

```lua
{% load static %} 
<img src="{% static 'my_app/example.jpg' %}">
```

In this reading, you learned how to use the template inheritance technique to build multiple templates with a consistent layout. You were also introduced to the mechanism of serving static assets.