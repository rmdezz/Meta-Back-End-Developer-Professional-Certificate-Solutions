# What you know about HTTP

# HTTP and HTTPS

- HTTP stands for Hypertext Transfer Protocol and is one of the most widely used communication protocols for transferring data across the Internet.
- **HTTP and HTTPS are used to browse webpages, view images, or submit a form.**
- Communication over HTTP requires at least two parts: the client who requests information and the server who responds to this request and serves the content.
- HTTPS is a secured version of HTTP that encrypts data before it starts its journey to the server.

```lua
Example:

User requests a webpage through the browser

Browser (Client) ---> Server (Responds to request)
```

# HTTP Methods

- There are five commonly used HTTP methods:
    - GET retrieves a resource
    - POST sends data to the server and creates a record
    - PUT updates the whole resource
    - PATCH updates a part of the resource
    - DELETE deletes a resource
    
    ```lua
    Example:
    
    GET request for a resource
    
    Browser (Client) ---> Server (Responds with resource)
    ```
    

# HTTP Requests

- An HTTP request contains information that a user's browser sends as encoded data.
- A typical HTTP request includes the following:
    - HTTP version type (e.g. 1.1 or 2.0)
    - URL or path
    - HTTP method
    - HTTP request headers
    - Optional HTTP body

```lua
Example:

Browser (Client) sends a request with the following data:

HTTP Version: 1.1
URL: https://www.example.com/page
Method: GET
Request Headers: [Accept: text/html]
Body: [empty]

Server (Responds with the requested resource)
```

# HTTP Responses

- An HTTP response consists of information that the browser uses to display the content and the response body.
- The response includes the following:
    - The requested resource
    - Length of the content
    - Content type
    - Cookies
    - ETags
    - Last modified time
    - HTTP status codes

```lua
Example:

Server responds to a request with the following data:

HTTP Version: 1.1
Status Code: 200 OK
Response Headers: [Content-Type: text/html, Content-Length: 1234]
Body: [html content of the requested resource]

Browser (Client) receives the response and displays the content.
```

# HTTP Status Codes

- HTTP status codes provide extra information to the browser about the resource.
- Some of the most commonly used status codes are:
    - 200 and 201 for successful responses
    - 400 and 401 for client error responses
    - 500 for server error codes
- The same status code can convey different messages in different contexts.

```lua
Example:

Server responds to a GET request with a 200 status code:

HTTP Version: 1.1
Status Code: 200 OK
Response Headers: [Content-Type: text/html, Content-Length: 1234]
Body: [html content of the requested resource]

The browser receives the response and displays the content.
```

# Conclusion

- This video recap of HTTP and HTTPS covered fundamental concepts for developing sustainable and manageable APIs.
- Topics covered include: HTTP and HTTPS communication, HTTP methods, HTTP requests, HTTP responses, and HTTP status codes.