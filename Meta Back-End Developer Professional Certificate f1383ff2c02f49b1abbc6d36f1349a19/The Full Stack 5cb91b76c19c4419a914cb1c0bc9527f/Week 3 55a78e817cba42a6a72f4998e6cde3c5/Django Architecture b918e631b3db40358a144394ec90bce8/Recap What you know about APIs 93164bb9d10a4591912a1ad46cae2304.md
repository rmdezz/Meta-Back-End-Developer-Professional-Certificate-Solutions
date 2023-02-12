# Recap: What you know about APIs

# Introduction

- Communication between different parts of an application is made possible by APIs.
- A refresher on APIs will help in upcoming sections of this full-stack course.

# HTTP and HTTPS

- You learned about the basics of HTTP and HTTPS communication in the API course.
- HTTP (Hypertext Transfer Protocol) is used to make requests and receive responses in web communication.
- HTTPS (HTTP Secure) is the encrypted version of HTTP and is more secure as data is encrypted on both client and server side.

# HTTP Methods and Status Codes

- You learned about the different HTTP methods that can be used to make API calls, such as GET, POST, PUT, and DELETE.
- You also learned about HTTP status codes, which give more information about the current HTTP request and its status. For example:
    
    
    | Status Code | Description |
    | --- | --- |
    | 200 | OK - The request was successful. |
    | 201 | Created - The request was successful and a resource was created. |
    | 204 | No Content - The request was successful, but there is no representation to return (i.e. the response is empty). |
    | 400 | Bad Request - The request could not be understood or was missing required parameters. |
    | 401 | Unauthorized - Authentication failed or user does not have permissions for the requested operation. |
    | 403 | Forbidden - Authentication succeeded, but the authenticated user does not have access to the requested resource. |
    | 404 | Not Found - The requested resource could not be found. |

# RESTfulness and Tools

- You learned about RESTfulness, which stands for Representational State Transfer, and the naming conventions used in API development.
- You also learned about tools that are essential for API development, such as Insomnia, a powerful REST API client.

# API Development Principles

- You covered the principles of API development, including REST best practices, security, authentication, authorization, and access control.
- You also learned about XML and JSON response types and how to organize your projects.

# Debugging and Mocking

- You learned about debugging your APIs, such as using the built-in debugging tools in VS Code and the Django Debugging Toolbar.
- You also learned about API mocking, which is a great way to imitate a real API endpoint for testing and development purposes.

# Django Rest Framework (DRF)

- You learned about the Django Rest Framework (DRF), which is a Django utility app that helps in creating APIs.
- You learned how to serialize your database models, convert, validate, and render data using DRF.
- You learned about different types of routers in DRF and the built-in renderer object.

# Filtering, Ordering, Searching, and Pagination

- You learned about filtering, ordering, searching, and pagination in APIs.
- Filtering is used to allow client applications to access specific data by passing query strings.
- Ordering allows you to order API results in ascending or descending order.
- Searching allows you to search for specific data in APIs.
- Pagination allows you to chunk results and control the number of items displayed per page.

# Caching and Security

- You learned about caching, which is a way to optimize overall performance by serving saved results instead of creating a fresh one every time it is requested.
- You also learned about data sanitation and API security, which is crucial as APIs give third-party clients access to your databases.
- You learned how to build token-based authentication in DRF and create different user roles for access control.
- You also learned about API throttling and how to control the frequency of API access.

# Conclusion

In conclusion, APIs are like bridges that connect the different components of an application together and integrate them into a single unit. Your API knowledge is important in full-stack development, so it's important to keep API knowledge up to date.

Revisit API course material if needed before proceeding with this course.