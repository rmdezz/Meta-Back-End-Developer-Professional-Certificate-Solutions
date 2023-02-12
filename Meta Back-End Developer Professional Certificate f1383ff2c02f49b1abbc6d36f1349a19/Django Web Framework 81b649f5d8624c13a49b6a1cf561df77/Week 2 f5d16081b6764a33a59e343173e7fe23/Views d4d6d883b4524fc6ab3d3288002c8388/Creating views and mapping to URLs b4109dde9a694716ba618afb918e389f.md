# Creating views and mapping to URLs

# Introduction

- In this video, you will learn about URL configuration in Django and how it's used to map URLs to views.
- You will explore the URL configuration file, urls.py, and learn why it exists at both the project and app levels.
- Finally, you will learn how to reference the urls.py file at the app level using the include function.

# URL Configuration

- To design URLs for an app, you create a Python module informally called a URLconf or URL configuration.
- The URL configurations used by the view functions in Django are created and updated in the urls.py file.
- **Django by default creates a urls.py file at the project level. But additionally, it's best practice to create a urls.py at the app level.**
- This way, the respective URLs for an app are clustered. But the project also needs to know what URLs are used inside each app.
    
    ![Screenshot 2023-01-23 at 7.47.57 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_7.47.57_PM.png)
    

# Inheriting URLs

- For example, in Django, when a user makes a request for a URL, this request is first handled by the urls.py file at the project level.
    
    ![Screenshot 2023-01-23 at 7.50.05 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_7.50.05_PM.png)
    
- Django looks for the variable URL patterns. However, the code that contains the logic for the URL mapping is at the app level.
    
    ![Screenshot 2023-01-23 at 7.50.37 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_7.50.37_PM.png)
    
- You need a way to tell Django to also check the urls.py file at the app level. You do this by using the include function.
    
    ![Screenshot 2023-01-23 at 7.51.14 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_7.51.14_PM.png)
    
- In the urls.py file at the project level, you create a new path inside the URL patterns list. Then inside the path function, you pass a reference to the app level urls.py file as the view argument.
    
    ![Screenshot 2023-01-23 at 7.51.57 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_7.51.57_PM.png)
    

# Example

- To demonstrate this concept, an example of a homepage for the Little Lemon restaurant is used.
- First step is to open the views.py file to create a view function and return a response containing a string "Welcome to the Little Lemon restaurant"
- Next step is to create a file inside the app called urls.py and import the path function from the Django dot URLs
- Then create a sequence called URL patterns and add the path function to it, passing an empty string followed by the location and the name of the view function, to map the URLs to the relevant view function.
- Finally, the app level [urls.py](http://urls.py/) file needs to be referenced in the project level [urls.py](http://urls.py/) file using the include function, so that the project level can access the app level URLs. This allows the user to see the message "Welcome to the Little Lemon restaurant" when they access the local host URL.

![Screenshot 2023-01-23 at 8.01.33 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_8.01.33_PM.png)

![Screenshot 2023-01-23 at 8.00.36 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_8.00.36_PM.png)

![Screenshot 2023-01-23 at 8.01.20 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_8.01.20_PM.png)

It's important to note that if the development server is already running on the same port, it will give an error message, "That port is already in use." To solve this, you need to stop the running server or choose a different port to run the server on.

![Screenshot 2023-01-23 at 8.03.19 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_8.03.19_PM.png)

### Changing port

![Screenshot 2023-01-23 at 8.03.52 PM.png](Creating%20views%20and%20mapping%20to%20URLs%20b4109dde9a694716ba618afb918e389f/Screenshot_2023-01-23_at_8.03.52_PM.png)