# Project structure and API routes

# Introduction

This reading is an overview of the scope of the project, all the necessary endpoints, and notes that you will have to implement in the final project. This reading will help you to successfully complete the project so read it carefully and reference it while developing your API project to help you keep on track.

# Scope

You will create a fully functioning API project for the Little Lemon restaurant **so that the client application developers can use the APIs to develop web and mobile applications.** 

People with different roles will be able to browse, add and edit menu items, place orders, browse orders, assign delivery crew to orders and finally deliver the orders.

The next section will walk you through the required endpoints with an authorization level and other helpful notes. Your task is to create these endpoints by following the instructions.

# Structure

You will create one single Django app called LittleLemonAPI and implement all API endpoints in it. Use pipenv to manage the dependencies in the virtual environment. Review the video about [Creating a Django Project using pipenv.](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/sn2Ez/video-subtitles)

# Function or class-based views

You can use function- or class-based views or both in this project. Follow the proper API naming convention throughout the project. Review the video about [Function- and class-based views](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/4BASB/video-subtitles) as well as the video about [Naming conventions](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/1jSCM/video-subtitles).

# User Groups

Create the following two user groups and then create some random users and assign them to these groups from the Django admin panel.

- Manager
- Delivery crew

Users not assigned to a group will be considered customers. Review the video about [User roles](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/12F4H/video-subtitles).

# Error check and proper status codes

You are required to display error messages with appropriate HTTP status codes for specific errors. 

These include when someone requests a non-existing item, makes unauthorized API requests, or sends invalid data in a **POST**, **PUT** or **PATCH** request. Here is a full list.

| HTTP Status code | Reason |
| --- | --- |
| 200 - Ok | For all successful GET, PUT, PATCH and DELETE calls |
| 201 - Created | For all successful POST requests |
| 403 - Unauthorized | If authorization fails for the current user token |
| 401 – Forbidden | If user authentication fails |
| 400 – Bad request | If validation fails for POST, PUT, PATCH and DELETE calls |
| 404 – Not found | If the request was made for a non-existing resource |

# API Endpoints

Here are all the required API routes for this project grouped into several categories.

### **User registration and token generation endpoints**

You can use Djoser in your project to automatically create the following endpoints and functionalities for you.

| Endpoint | Role | Method | Purpose |
| --- | --- | --- | --- |
| /api/users | No role required | POST | Creates a new user with name, email and password |
| /api/users/users/me/
 | Anyone with a valid user token | GET | Displays only the current user |
| /token/login/ | Anyone with a valid username and password | POST | Generates access tokens that can be used in other API calls in this project |

When you include Djoser endpoints, Djoser will create other useful endpoints as discussed in the [Introduction to Djoser library for better authentication](https://www.coursera.org/learn/apis/lecture/bldmJ/introduction-to-djoser-library-for-better-authentication) video.

# Menu-items Endpoints

| Endpoint | Role | Method | Purpose |
| --- | --- | --- | --- |
| /api/menu-items | Customer, delivery crew | GET | Lists all menu items. Return a 200 – Ok HTTP status code |
| /api/menu-items | Customer, delivery crew
 | POST, PUT, PATCH, DELETE | Denies access and returns 403 – Unauthorized HTTP status code |
| /api/menu-items/{menuItem} | Customer, delivery crew
 | GET | Lists single menu item |
| /api/menu-items/{menuItem} | Customer, delivery crew | POST, PUT, PATCH, DELETE | Returns 403 - Unauthorized |
|  |  |  |  |
| /api/menu-items | Manager | GET | Lists all menu items |
| /api/menu-items | Manager | POST | Creates a new menu item and returns 201 - Created |
| /api/menu-items/{menuItem} | Manager | GET | Lists single menu item |
| /api/menu-items/{menuItem} | Manager | PUT, PATCH | Updates single menu item |
| /api/menu-items/{menuItem} | Manager | DELETE | Deletes menu item |

# **User group management endpoints**

| Endpoint | Role | Method | Purpose |
| --- | --- | --- | --- |
| /api/groups/manager/users | Manager | GET | Returns all managers |
| /api/groups/manager/users
 | Manager | POST | Assigns the user in the payload to the manager group and returns 201-Created |
| /api/groups/manager/users/{userId} | Manager | DELETE | Removes this particular user from the manager group and returns 200 – Success if everything is okay.
If the user is not found, returns 404 – Not found |
| /api/groups/delivery-crew/users | Manager | GET | Returns all delivery crew |
| /api/groups/delivery-crew/users
 | Manager | POST | Assigns the user in the payload to delivery crew group and returns 201-Created HTTP |
| /api/groups/delivery-crew/users/{userId} | Manager | DELETE | Removes this user from the manager group and returns 200 – Success if everything is okay.
If the user is not found, returns  404 – Not found |

# **Cart management endpoints**

| Endpoint | Role | Method | Purpose |
| --- | --- | --- | --- |
| /api/cart/menu-items | Customer | GET | Returns current items in the cart for the current user token |
| /api/cart/menu-items
 | Customer
 | POST | Adds the menu item to the cart. Sets the authenticated user as the user id for these cart items |
| /api/cart/menu-items
 | Customer
 | DELETE | Deletes all menu items created by the current user token |

# **Order management endpoints**

| Endpoint | Role | Method | Purpose |
| --- | --- | --- | --- |
| /api/orders | Customer | GET | Returns all orders with order items created by this user |
| /api/orders
 | Customer
 | POST | Creates a new order item for the current user. Gets current cart items from the cart endpoints and adds those items to the order items table. Then deletes all items from the cart for this user. |
| /api/orders/{orderId}
 | Customer | GET | Returns all items for this order id. If the order ID doesn’t belong to the current user, it displays an appropriate HTTP error status code. |
| /api/orders | Manager | GET | Returns all orders with order items by all users |
| /api/orders/{orderId}
 | Customer
 | PUT, PATCH | Updates the order. A manager can use this endpoint to set a delivery crew to this order, and also update the order status to 0 or 1.
If a delivery crew is assigned to this order and the status = 0, it means the order is out for delivery.
If a delivery crew is assigned to this order and the status = 1, it means the order has been delivered. |
| /api/orders/{orderId} | Manager | DELETE | Deletes this order |
| /api/orders | Delivery crew | GET | Returns all orders with order items assigned to the delivery crew |
| /api/orders/{orderId} | Delivery crew
 | PATCH | A delivery crew can use this endpoint to update the order status to 0 or 1. The delivery crew will not be able to update anything else in this order. |

# **Additional step**

Implement proper filtering, pagination and sorting capabilities for **/api/menu-items** and **/api/orders** **endpoints**. Review the videos about [Filtering and searching](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/h7QUx/video-subtitles) and [Pagination](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/mEYFj/video-subtitles) as well as the reading [More on filtering and pagination](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/supplement/oCL3M).

# **Throttling**

Finally, apply some throttling for the authenticated users and anonymous or unauthenticated users. Review the video [Setting up API throttling](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/rPE4B/video-subtitles) and the reading [API throttling for class-based views](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/supplement/1h6WO) for guidance.

# **Conclusion**

Now that you have a better idea of the scope of this project with the essential API endpoints, it’s time to start coding. Good luck!