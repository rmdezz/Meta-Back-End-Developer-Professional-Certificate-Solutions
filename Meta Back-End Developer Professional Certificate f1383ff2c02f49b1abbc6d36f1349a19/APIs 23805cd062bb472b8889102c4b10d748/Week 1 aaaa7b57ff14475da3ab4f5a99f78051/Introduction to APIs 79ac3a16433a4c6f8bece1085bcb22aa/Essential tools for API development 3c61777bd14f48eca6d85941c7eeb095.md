# Essential tools for API development

## **Introduction**

- To be an efficient developer, you need the right tools.
- This video will introduce you to command line and graphical tools for testing APIs, with a practical demonstration using Insomnia.
- These tools are cross-platform and can be used on Windows, macOS, and Linux.

## **Tools for Testing APIs**

### **curl**

- curl is a well-known tool for making HTTP calls from the command line.
- Available for all major operating systems and does not have a graphical tool.
- Example usage:
    - Open PowerShell or terminal and type curl followed by API URI.
    - To send a HTTP GET request:
        
        ```bash
        curl https://postman-echo.com/get
        
        ```
        
    - To send a HTTP POST request:
        
        ```bash
        curl -X POST -d "data=value" https://postman-echo.com/post
        
        ```
        

### **Postman**

- A cross-platform desktop tool for testing and debugging APIs.
- Has an advanced graphical interface and a web version.
- Learn more from the Postman website and additional readings.

### **Insomnia REST Client**

- A powerful REST API client for storing, organizing, and executing REST API requests.
- Free, cross-platform, and has a user-friendly interface.
- Download and install Insomnia from the link in additional readings.

## **Using Insomnia**

- Insomnia saves all requests in a request collection.
- To get started:
    1. Click on the Create button and select Request collection.
    2. Give it a name and click on Create.
    3. To create an API request, click on the Plus icon and select HTTP Request.
    4. Change the default request name to something more personal.
    5. Select the type of HTTP method (GET or POST).
    6. Enter the API URL in the text box.
    7. To input data for a POST request, click on the body tab and select Form URL Encoded or JSON.
    8. Layout arguments on the left and values on the right.
    9. Click on the Send button to display the output.

## **Recap**

- This video introduced you to the tools curl, Postman, and Insomnia for testing APIs.
- Insomnia is a great tool for playing with APIs, where you can create and save multiple requests.
- By using these tools, you can become a more competent and efficient developer.