# Naming conventions

# ****Best Practices for API Endpoint Naming****

When designing REST APIs, **naming conventions play an important role in making the API user-friendly and easy to understand.** Here are some best practices to follow when naming API endpoints:

## ****Use Lowercase URI Formatting****

- Use lowercase letters in API endpoint names and separate multiple words with hyphens (e.g. **`/orders`**, **`/order-items`**).
- Exception: When using variables such as **`userId`** or **`orderId`** in API endpoints, use camel case and wrap them in curly braces (e.g. **`/orders/{orderId}`**, **`/users/{userId}`**).

## **Indicate Hierarchical Relationships with Forward Slashes**

- Use forward slashes to indicate the hierarchical relationship between related objects (e.g. **`/library/books/{bookId}/author`**, **`/customers/{customerId}/orders`**).

## **Use Nouns for Resource Names**

- Use nouns to represent resources in API endpoints (e.g. **`/books`**, **`/book/{bookId}`**) instead of verbs (e.g. **`getAllBooks`**, **`getUser`**).
- Avoid using standard CRUD operations in API endpoints (e.g. **`/create`**, **`/read`**, **`/update`**, **`/delete`**). Instead, use the appropriate HTTP request method (e.g. **`GET`**, **`POST`**, **`PUT`**, **`DELETE`**) with the endpoint to perform the necessary manipulation.

## **Avoid File Name Extensions**

- Do not use file name extensions in API endpoints (e.g. **`/orders/{orderId}.json`**). Instead, use query parameters to specify the desired format (e.g. **`/orders/{orderId}?format=json`**).

## **Use Query Parameters for Data Types**

- Use query parameters to filter collections or perform searches (e.g. **`/menu-items?category=appetizer`**, **`/orders?customerId={customerId}`**).

## **Don't Use a Trailing Slash**

- Do not add a trailing slash to the end of API endpoints (e.g. **`/orders/`** or **`/orders/{orderId}/`**).

## **Follow a Consistent Naming Strategy**

- Follow a consistent naming strategy and standard API naming conventions to improve the overall quality and usability of the API.

# Examples

```lua
# Fetch all orders
GET /orders

# Fetch a specific order
GET /orders/{orderId}

# Fetch menu items for a specific order
GET /orders/{orderId}/menu-items

# Fetch orders for a specific customer
GET /customers/{customerId}/orders

# Fetch author for a specific book
GET /library/books/{bookId}/author

# Fetch all books written by a specific author
GET /library/authors/{authorId}/books

# Fetch menu items filtered by category
GET /menu-items?category=appetizer

# Fetch order data in JSON format
GET /orders/{orderId}?format=json
```

By following these best practices, you can create well-designed and user-friendly API endpoints that are easy to understand and maintain.