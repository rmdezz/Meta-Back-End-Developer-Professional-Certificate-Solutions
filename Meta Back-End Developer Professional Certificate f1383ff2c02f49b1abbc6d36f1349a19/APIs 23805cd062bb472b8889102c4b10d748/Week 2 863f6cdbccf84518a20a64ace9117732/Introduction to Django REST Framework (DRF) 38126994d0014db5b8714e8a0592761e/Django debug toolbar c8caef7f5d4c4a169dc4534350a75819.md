# Django debug toolbar

The Django Debug Toolbar is a must-have tool for every Django developer. In this video, we'll be learning how to integrate it into your Django projects and take advantage of its many features.

# Installing the Django Debug Toolbar

To install the Django Debug Toolbar, use pip or pipenv in your project's terminal window. 

First, activate the virtual environment with **`pipenv shell`**, then run **`pipenv install Django-debug-toolbar`**.

![Screenshot 2023-02-01 at 7.35.36 PM.png](Django%20debug%20toolbar%20c8caef7f5d4c4a169dc4534350a75819/Screenshot_2023-02-01_at_7.35.36_PM.png)

Next, add the debug toolbar to the installed apps section in the **`settings.py`** file. 

![Screenshot 2023-02-01 at 7.39.28 PM.png](Django%20debug%20toolbar%20c8caef7f5d4c4a169dc4534350a75819/Screenshot_2023-02-01_at_7.39.28_PM.png)

Also, add a special URL pattern in your project to map the debug toolbar and a middleware called **`debug_toolbar.middleware.DebugToolbarMiddleware`** in the middleware section in the **`settings.py`** file. 

![Screenshot 2023-02-01 at 7.39.42 PM.png](Django%20debug%20toolbar%20c8caef7f5d4c4a169dc4534350a75819/Screenshot_2023-02-01_at_7.39.42_PM.png)

Finally, include **`127.0.0.1`** in the **`internal IPs`** section in the **`settings.py`** file.

![Screenshot 2023-02-01 at 7.39.55 PM.png](Django%20debug%20toolbar%20c8caef7f5d4c4a169dc4534350a75819/Screenshot_2023-02-01_at_7.39.55_PM.png)

# **Using the Django Debug Toolbar**

Once you've installed the Django Debug Toolbar, visit any endpoint (e.g. **`localhost:8000/api/books`**). You should now see the debug toolbar on the right side of the screen, containing information about your current project setup, requests, and database queries.

![Screenshot 2023-02-01 at 7.42.33 PM.png](Django%20debug%20toolbar%20c8caef7f5d4c4a169dc4534350a75819/Screenshot_2023-02-01_at_7.42.33_PM.png)

You can hide the debug toolbar by clicking on the hide link at the top of the toolbar. You can also enable and disable any section of the toolbar using the checkboxes beside each of them.

# **Debug Toolbar Features**

The Django Debug Toolbar has several sections, let's take a closer look at some of the important ones:

## **Settings Section**

The settings section displays all the settings you have in your **`settings.py`** file and other settings used throughout the project and the installed apps. You can easily override a setting by copying its name and value from this section and adding it to the **`settings.py`** file with a new value.

## **Headers Section**

The headers section includes all the header information sent in the request and those generated in the response.

## **SQL Queries Section**

The SQL queries section is one of the most useful sections in the Django Debug Toolbar. It shows the list of SQL queries executed for the endpoint. This is where you often check for performance tuning and optimization. You can easily detect if more than required SQL queries are running and take the necessary steps to fix them.

## **Static Files Section**

The static files section displays all the static files loaded for the current request and those used by the installed apps. Although developers usually don't serve static files from API requests, it's important to know about this section.

## **Cache Section**

The cache section displays applications that use cache. You'll learn more about cache later in this course, but for now, know that cache helps reduce load to a great extent.

## **Profiling Section**

The profiling section, which is unchecked by default, displays the complete call stack. When you make a request, the code execution flow begins in one file, invokes another function, and goes on until it reaches your function or class-based views and generates the response to display. The profiling section contains this full code execution flow.

# **Conclusion**

In this video, you learned about the Django Debug Toolbar, an important tool for debugging and optimizing your API project. You should now be able to include it in your project and use some of its important sections. Note that the Django Debug Toolbar will only be visible during development time when using the browser API and will not show when making API calls in the production environment or when returning data