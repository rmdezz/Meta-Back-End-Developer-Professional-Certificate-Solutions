# RESTfulness

# What is REST?

REST stands for Representational State Transfer, **it is an architectural style for designing APIs.**

# Key constraints of REST API

REST APIs have several key constraints that make them RESTful.

- Client-Server architecture
- Stateless
- Cacheable
- Layered System
- Uniform Interface
- Code on Demand (optional)

## Client-server architecture

In REST, there should be a clear separation between the client and the server. The client requests resources from the server and the server provides the requested resources.

## Stateless

REST APIs are stateless, which means the server does not store any information about the client making the request. **All information needed to process the request must be included in each request.**

## Cacheable

REST APIs should be cacheable, which means that **responses can be saved and reused to reduce server load.**

## Layered system

REST APIs should follow a layered system architecture. This means that the system can be split into multiple layers and layers can be added or removed as needed.

## Uniform Interface

REST APIs should have a uniform interface for accessing resources. This means that resources should be accessed using a consistent set of methods and there should be a standard way to represent resources, such as JSON or XML.

## Code on demand

REST APIs may provide code that can be executed by the client to improve the response.

# Resource types

## Resources

Resources are the core part of a REST API and **represent the data being accessed.**

## Examples

- Manager wants to see all orders:
API call: little.lemon/orders
Resource type: List of order objects
- Manager wants to see specific information about an order:
API call: little.lemon/orders/16
Resource type: Order object
- Manager wants to see customer information for an order:
API call: little.lemon/orders/16/customer
Resource type: Customer object
- Manager wants to see menu items for an order:
API call: little.lemon/orders/16/menu_items
Resource type: Menu item object
- Customer wants to browse the menu:
API call: little.lemon/menu_items
Resource type: Menu item object
- Customer wants to browse food items from a specific category:
API call: little.lemon/menu_items?category=appetizers
Resource type: Menu item object

# Statelessness in REST API

REST APIs are stateless, which means that the server does not store any information about the client.

**Example:**
If a manager retrieves information about order 16 and then wants to see the menu items for that order, they cannot simply send a follow-up HTTP request to the endpoint /menu_items. The server does not remember that the previous request was for a specific order. To get the menu items for a specific order, the manager must explicitly supply the order number in the request, for example: /orders/16/menu_items.

# Conclusion

In this video, you learned about the basics of REST APIs and the key constraints that make them RESTful. You also learned about resource types and the importance of statelessness in REST APIs. These concepts will help you build APIs that are easy to use and maintain.