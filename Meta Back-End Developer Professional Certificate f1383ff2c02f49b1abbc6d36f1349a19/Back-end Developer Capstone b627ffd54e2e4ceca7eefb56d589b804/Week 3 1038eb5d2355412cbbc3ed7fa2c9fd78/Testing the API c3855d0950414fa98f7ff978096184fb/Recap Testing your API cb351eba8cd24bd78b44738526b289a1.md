# Recap: Testing your API

# ****Introduction****

Before releasing the API to the end user, it is important that the developer test the API endpoints to check if the desired responses are obtained.

There are various API testing tools available, both for commercial use and as open-source apps. Insomnia is a free-to use tool for testing the REST API performance.

# ****Prerequisites****

- Install Django and the Django REST Framework in the current Python environment.
- Create a Django project named **LittleLemon** using the **django-admin** command.
- Inside the Django project, create a Django app with the name **LittleLemonAPI**.
- Add the code **'rest_framework'**, and **'LittleLemonAPI'** to the **INSTALLED_APPS** list inside the **settings.py** file.
- The views for the **Menu** API are defined, and its routes are configured.

# ****Install Insomnia****

Insomnia is available as a browser extension for most of the popular browsers. However, it has limited functionality as compared to the desktop application. Hence, you should download and install Insomnia from  [https://insomnia.rest/download](https://insomnia.rest/download).

Launch the Insomnia app. You'll find three options in the top menu: **Design**, **Debug**, and **Test**. Make sure that the Debug option is active.

You use the Design window to design API specification documents and the Test window to write the unit tests. It is from the Debug window that you visit the endpoints of your API and test the responses.

Make sure that your Django application is running.

The insomnia interface is arranged in three panels. The left panel shows the requests issued so far.

In the middle panel, you enter various parameters such as body parameters, query parameters, header, etc.

Insomnia renders the responses in the right panel.

Above the middle panel, you have a drop-down menu from which you can choose the type of HTTP request and a textbox to enter the URL.

The top of the right panel displays the response's status code. Here is a typical view of the Insomnia app:

![Untitled](Recap%20Testing%20your%20API%20cb351eba8cd24bd78b44738526b289a1/Untitled.png)

You have defined the **SingleMenuItemView** class that handles **GET**, **PUT** and **DELETE** requests for a given ID.

To test the functionality of retrieving a single menu item, change the URL by appending the item’s ID and send the request to the Django server. The response panel shows the details with 200 OK status code on top.

The **SingleMenuItemView** also preforms the POST request operations. Choose the POST option, enter the value for the model fields. On sending the request, new instance is added to the model.

![Untitled](Recap%20Testing%20your%20API%20cb351eba8cd24bd78b44738526b289a1/Untitled%201.png)

You can confirm that a new instance is created, by visiting the **GET** endpoint again.

Similarly, you can test the **PUT** and **DELETE** requests with Insomnia.

If you have secured your API with the **token authorization** scheme, you will need to enter the **bearer token** in **Auth** tab. Obtain the token from the **api-token-auth/** endpoint.

![Untitled](Recap%20Testing%20your%20API%20cb351eba8cd24bd78b44738526b289a1/Untitled%202.png)

Use the token for all the subsequent operations.

![Untitled](Recap%20Testing%20your%20API%20cb351eba8cd24bd78b44738526b289a1/Untitled%203.png)

In this reading, you learned how to use Insomnia to test your DRF API.