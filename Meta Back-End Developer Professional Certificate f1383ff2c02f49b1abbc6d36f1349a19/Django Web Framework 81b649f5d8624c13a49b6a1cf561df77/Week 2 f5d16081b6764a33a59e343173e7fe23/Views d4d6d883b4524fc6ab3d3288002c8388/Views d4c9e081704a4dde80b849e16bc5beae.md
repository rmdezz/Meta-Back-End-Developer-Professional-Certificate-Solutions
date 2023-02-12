# Views

# Introduction

In this video, you will learn about views in Django and how developers use them to process HTTP requests and return an HTTP response.

Django views are functions designed to handle a web request and return a web response such as an HTML document. To demonstrate this concept, we will explore an HTTP request response scenario using examples of a static file and a dynamic file.

# Static File

For a static file with no dynamic content, the HTTP request just needs to map to where the file is located and return that page for rendering. As the static page does not change, nothing else is needed.

For example, suppose the page is located at the address **`littlelemon.com/index.html`**, the web server will process the request and return a response containing the page index.html to the browser, which then renders the content.

![Screenshot 2023-01-23 at 7.16.18 PM.png](Views%20d4c9e081704a4dde80b849e16bc5beae/Screenshot_2023-01-23_at_7.16.18_PM.png)

![Screenshot 2023-01-23 at 7.17.19 PM.png](Views%20d4c9e081704a4dde80b849e16bc5beae/Screenshot_2023-01-23_at_7.17.19_PM.png)

# Dynamic File

When building a dynamic website using Django, **you will need to write a Python function to create a view.** The view function takes an HTTP request object as its first parameter, named request. The view function is created inside the views.py file, and returns the HTML.

For example, you would create a function called home, and inside of it, you would:

- Import the class HTTP response from the django.http module.
- Create a variable to store a string containing the HTML to be returned.
- Use the return statement with the HTTP response object to return the variable containing the code.

![Screenshot 2023-01-23 at 7.18.02 PM.png](Views%20d4c9e081704a4dde80b849e16bc5beae/Screenshot_2023-01-23_at_7.18.02_PM.png)

Each view function takes an HTTP Request object as its first parameter named request.

![Screenshot 2023-01-23 at 7.23.45 PM.png](Views%20d4c9e081704a4dde80b849e16bc5beae/Screenshot_2023-01-23_at_7.23.45_PM.png)

You can also perform other programming logic inside of view functions such as:

- Processing data for email and forms.
- Retrieving data from a database.
- Transforming data.
- Rendering templates.

<aside>
🤔 It's important to know that the name you give the **view function** doesn't matter, the function doesn't need to be named in a certain way for Django to recognize it. It's good practice to name the function something that clearly indicates what the function does.

</aside>

# Routing

Creating a view function is not enough to make the request response work. The view function needs to be mapped to a URL so that when the request to the URL is made, the view function gets called. This process of mapping a URL to a view function is known as routing.

![Screenshot 2023-01-23 at 7.28.18 PM.png](Views%20d4c9e081704a4dde80b849e16bc5beae/Screenshot_2023-01-23_at_7.28.18_PM.png)

To set up this routing, you will need to create a new file inside the app directory called urls.py. Inside the urls.py file, you will:

- Import the path function
- Import the views.py file from the app directory
- Create a path for the view function
    
    ![Screenshot 2023-01-23 at 7.29.14 PM.png](Views%20d4c9e081704a4dde80b849e16bc5beae/Screenshot_2023-01-23_at_7.29.14_PM.png)
    

# Conclusion

In summary, views in Django are functions designed to handle a web request and return a web response such as an HTML document. 

Creating a view function is not enough to make the request response work, you also need to set up routing to map URLs to views by creating a [urls.py](http://urls.py/) file. 

The [views.py](http://views.py/) file should be created inside the app directory as a best practice. You will learn more about routing and the difference between the project's [urls.py](http://urls.py/) and the app's [urls.py](http://urls.py/) later in this course.