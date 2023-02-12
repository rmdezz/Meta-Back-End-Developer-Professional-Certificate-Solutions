# Book list API project

# **Introduction**

- Welcome to the Django API project where you will be creating a simple API to manage books in a bookstore.
- The goal is to develop APIs that allow you to add, edit, view, and delete books from a database.

# **Creating a Django Model**

- To store books in the database, you need to create a Django Model that defines the data and how it will be stored.
- For this project, the model should contain the following fields:
    - Title: a char field with a max length of 255
    - Author: another char field with a max length of 255
    - Price: a decimal field with a maximum of five digits and two decimal places
    - Inventory: an optional positive small integer field to indicate if a book is in stock or not

# **Creating API Endpoints**

- To view all the books and a single book, you need to create two endpoints:
    - /api/books: will deliver all the books in the database
    - /api/books/<book_id>: will show a particular book
- If someone requests a book that doesn't exist, a 404 error message with the appropriate status code should be returned.
- For a successful request, the status code should be 200.

# **Creating a New Book**

- To create a new book, you need to send a HTTP POST request to the /api/books endpoint.
- Here's an example of a JSON payload with book title and author data:

```bash
{
  "title": "Django for Beginners",
  "author": "John Doe"
}
```

- For a successful request, it should return the newly created book with a status code 201.
- If any required data is missing, for example, the author's name, it should return an error message with HTTP status code 400.

# **Converting a Model to a JSON Response**

- The results of an API request are usually delivered as JSON or XML data.
- To convert a single model to a JSON response, you need to import the **`model_to_dict`** function from the **`Django.forms.models`** module and the **`JSONResponse`** class from the **`Django.http`** module.

# **Editing and Deleting a Book**

- To edit an existing book, you need to accept a HTTP PUT request to the /api/books/<book_id> endpoint.
- To delete an existing book, you need to send a HTTP DELETE request.
- You can create a URL pattern for this endpoint in your Django project as **`/api/books/<pk>`**.

# **Parsing the HTTP Body**

- Data is passed to the web server in the HTTP body as either a raw JSON string or a form URL-encoded string (payload).
- To access the individual elements of the HTTP request body, you can use the **`QueryDict`** class from the **`Django.http`** module to parse the request body to a Python dictionary.

```bash
request_data = QueryDict(request.body)
title = request_data.get('title')
author = request_data.get('author')
```

# **Conclusion**

- In this video, you learned how to create a Django Model to represent a database table, create API endpoints to view all books and a single book, convert a model to a JSON response, and edit, delete, and soft-delete books.
- You also learned how to parse the HTTP body to access data elements. With these concepts and tips, writing the actual working code should be straightforward.