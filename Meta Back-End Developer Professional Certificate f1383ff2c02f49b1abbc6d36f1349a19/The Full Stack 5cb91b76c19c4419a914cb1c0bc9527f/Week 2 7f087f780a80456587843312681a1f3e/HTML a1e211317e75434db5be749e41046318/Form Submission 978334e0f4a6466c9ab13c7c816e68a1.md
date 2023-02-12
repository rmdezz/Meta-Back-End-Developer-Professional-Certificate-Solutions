# Form Submission

- When you order products online, you fill out your address and credit card number, then click on an Order button to confirm the order.
- The web browser communicates with a web server using an HTTP request-response cycle, which means the browser sends requests to the server and the server sends back a response.
- It is also possible to send data as part of a request and this is how forms send data to the web server.

# HTTP Get Method

When the method attribute of the form element is set to GET, the form data is sent as part of the request URL. This means that the user data is appended to the end of the URL in the web browser navigation bar. The web server receives the HTTP GET request and extracts the form data from the URL.

While this is an easy way to submit data, it has three key problems:

- The length of a URL is limited to around 2,000 characters, which can vary depending on the web browser being used.
- The length of a requested URL is also limited on some web servers.
- The data is included as part of the URL, which means that it is stored in the web browser history and possibly in the request logs on the web server. **This poses a major privacy and security risk if sensitive information such as addresses or credit card numbers are being transmitted.**

## HTTP Post Method

When the method attribute of the form is set to POST, the form data is inserted into the content of the HTTP request. When the submit button is pressed, it sends an HTTP POST request with the data contained in the body of the request. **The HTTP POST method is more secure than the HTTP GET method.**

However, to ensure complete security, HTTPS is used to encrypt the data so that only the sender and receiver can understand it. Once the web server receives the request, it processes it and sends back an HTTP response. If the request was successful, the response will direct the browser to a new webpage. If errors occur, the webpage can handle them in various ways, as explained in a previous video.

# Example: Login Form

Consider a login form that accepts a username and password, along with a Login button that submits the form to the web server.

- If the method attribute is set to GET, the form data is sent as part of the request URL.
- If the method attribute is set to POST, the form data is inserted into the content of the HTTP request.

In this example, it is recommended to use the POST method for the login form for better security.

You should now have a good understanding of how forms are sent to web servers and the difference between the GET and POST methods.