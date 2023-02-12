# Exercise: Testing the API using Insomnia

# ****Overview****

By now, you have the Django app with Menu API and table booking API built with Django REST framework, up and running.

This is the final exercise of this course. In this exercise, you will use Insomnia to test your API.

# ****Scenario****

You can perform CREATE, READ, UPDATE and DELETE operations with the browsable API provided by the Django REST framework. However, Insomnia is a more versatile API client with a lot of useful functionality.

# Steps

## Step 1

Download and install the Insomnia client app from [https://insomnia.rest/download](https://insomnia.rest/download).

## Step 2

Start the Django server.

Visit the browsable API URL of the Menu API to confirm the satisfactory functioning of the endpoints.

## Step 3

Open the Insomnia app that you installed in the step 1.

## Step 4

Create a new request. Enter the URL such as **`http://127.0.0.1:8000/api/menu-items/**.`

Choose the GET request.

In the responses panel, you will get the list of all the items in the Menu model.

## Step 5

To add a new item through the Insomnia interface, change the request type to POST, keep the same URL: **`http://127.0.0.1:8000/api/menu-items/`**

Enter the details of the new item in JSON format.

![Untitled](Exercise%20Testing%20the%20API%20using%20Insomnia%209d326f8108a44563ba1573b479fd3d23/Untitled.png)

## **Step 6**

To update any existing item data, select the request type to PUT, append the item id to the URL – for example **`http://127.0.0.1:8000/api/menu-items/5**.`

Enter the updated data for the item in JSON and send the request. The item is modified. You can confirm by issuing the GET request again.

## Step 7

To test the DELETE operation, change the method type to DELETE, the URL should contain the id of the item to be deleted. Simply click the send button.

The item of the given id will be deleted from the model. To confirm, issue the GET request again.

# ****Conclusion****

In this exercise, you tested the GET, POST, PUT and DELETE operations on your Menu API.