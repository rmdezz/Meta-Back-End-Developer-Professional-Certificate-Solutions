# Creating Requests and Responses

# Introduction

In this video, you will learn how to use Django's HTTP request and response objects to handle the request-response cycle in Django.

# The Request-Response Cycle in Django

The cycle begins when the user enters a URL in their web browser.

![Screenshot 2023-01-24 at 8.44.38 PM.png](Creating%20Requests%20and%20Responses%20bae0f6fdeae64fceb013783de13581f7/Screenshot_2023-01-24_at_8.44.38_PM.png)

The URL is sent to the web server where Django searches for a match inside the urls.py file.

![Screenshot 2023-01-24 at 8.45.06 PM.png](Creating%20Requests%20and%20Responses%20bae0f6fdeae64fceb013783de13581f7/Screenshot_2023-01-24_at_8.45.06_PM.png)

Once it finds the URL, it is mapped to its associated view. Inside the view file, the view function receives the HTTP request as a request object. 

![Screenshot 2023-01-24 at 8.46.52 PM.png](Creating%20Requests%20and%20Responses%20bae0f6fdeae64fceb013783de13581f7/Screenshot_2023-01-24_at_8.46.52_PM.png)

The view function then defines the appropriate HttpResponse and sends it back as a HttpResponse object. This response is processed by Django and the client receives the HttpResponse.

# ****Working with Django's Request and Response Objects****