# Consequences of poorly designed API project

# Introduction

Creating a good API project can be challenging. You need to stick to the conventions, write proper error checks in your code, perform security checks, and make sure that your APIs are using processing power and bandwidth optimally. This all takes time and proper planning. But what happens if you don’t properly plan and execute your APIs?

Let’s examine some of the consequences of a poorly designed API project.

# Data Breach

| Reasons | Consequences |
| --- | --- |
| Poor security checks in the code, no authentication or authorization checks, improper file permission, and not using SSL | The most significant risk of a poorly designed API project is a data breach. Sensitive data can leak if you don’t have proper security checks in your code or if you didn’t implement proper permissions for the files stored on the server.

Also, if you are not using SSL for your API endpoints, attackers can steal user data before it reaches your API web server.
Such mistakes can cause severe financial damage and trust issues. |

**Fix**: Add proper security checks in your code and create a solid authorization layer to prevent unauthorized access to your data. Always double-check these sensitive API endpoints before deploying them to production.

# Data corruption

| Reasons | Consequences |
| --- | --- |
| Poor security, no authentication or authorization checks, absence of data validation and sanitization of input data | Improper security checks and lack of a solid authorization layer can let any user with a valid authentication token access sensitive APIs and modify the data unexpectedly. Also, creating resources without proper validation checks can create malformed data in the database.
Such mistakes can cause severe data corruption and data loss beyond repair. |

**Fix**: Besides security checks and a solid authorization layer, an **API developer must validate and sanitize user data before processing and saving it.**

# Wastage of computing power and memory

| Reasons | Consequences |
| --- | --- |
| Unoptimized code, improper business logic, lack of data validation, unoptimized SQL queries or model relationships, lack of database indexes, and no caching. | Poorly written API code can consume unnecessary computing power and memory with unoptimized code, algorithms and business logic. Unoptimized code, lack of proper database indexing and absence of caching can cause a huge load on the database server by running redundant SQL queries, which slows the whole system down.
Such mistakes can end up increasing the cost of your API infrastructure. |

**Fix**: To avoid this, always spend time optimizing the code and double-checking your database-related code before deploying your APIs to production.

# Wastage of bandwith

| Reasons | Consequences |
| --- | --- |
| Absence of necessary caching header API code, lack of caching policy on the reverse proxy and on the web server, and lack of pagination and filtering. | If your API project doesn’t follow good API development practices like implementing caching, filtering and pagination can cause your APIs to deliver unnecessary data more times than what is required.
Such mistakes can cause bandwidth wasting and end up charging extra bills in your monthly invoice, as well as poor performance from your API endpoints. Besides, the client applications need to spend more resources and time filtering unnecessary data every time. |

**Fix**: To avoid this, always send proper caching headers with your API responses and implement filtering and pagination features so that the client application can request and receive only what they need.

# Bad user experience

| Reasons | Consequences |
| --- | --- |
| Not following the proper naming convention, not sending proper HTTP codes, not accepting Accept headers, absence of pagination, sorting, searching and filtering, and lack of proper error checking in code. | It creates a bad user experience. The client application developers must go through extra processing of the API data, extra code to create the final output, and a steeper learning curve to use your API, which was not necessary if the API was designed by following the standard conventions and best practices.
Not accepting the Accept headers means that the API client is not getting the API output in its required format. That will cause bad experiences because clients need extra time and unnecessary code to process the data on their end.   
Also, sending wrong HTTP status codes can cause unexpected errors on the client applications and a bad experience for the users who will use those applications. |

**Fix**: To avoid this, always follow the proper naming convention and implement data filtering, searching, sorting, searching and pagination features for your API endpoints. Always keep proper error checking in the code and write tests so that it doesn’t create unexpected 5XX errors on the server side.

# **Breaking client applications**

| Reasons | Consequences |
| --- | --- |
| Not following the proper versioning system | If you don't maintain the proper versioning system for your API project, it can immediately break backward compatibility, and the client application can stop working instantaneously.
The API can cause failure in the current client applications because your new API requires new request data and delivers new responses. So, their old code will not work anymore. They must refactor it and release a new version of their application as soon as possible.
Such disruption can cause a bad reputation and financial damage for both the API and client application developers. |

# **Failure to manage the app**

| Reasons | Consequences |
| --- | --- |
| Keeping everything in one big Django app, adding all business logic in the views. | Django apps can become big and become unmanageable over time if you keep adding functionalities in one single app. And then, adding new features or debugging an error will be painful and take extra time and effort.
Also, adding all business logic in the views file can lead to writing redundant code across multiple classes and function-based views.
Failure to manage an app over time leads to bad coding, patching of errors without test coverage and ultimately, poor performance from the APIs. |

**Fix**: Distribute the features and functionalities to multiple smaller Django apps in a decoupled way. Additionally, put some business logic in the models which can be reused by the other parts of your API project.

## **Conclusion**

Taking the time to properly design an API project from the start will save you time and effort over the course of a project. The consequences of a poorly designed API affect everyone who uses your API, including the API developers and client application developers.

The knowledge you gained in this reading will hopefully remind you of everything you need to keep in mind to make your future API projects successful.