# N-tier architecture

In application development, there are different parts that make up an application, such as the user interface, backend, business logic, and database. To make an application work, these parts need to communicate with each other effectively.

In this video, you will learn about the common architectures used in modern application development.

# Layers vs Tiers

In application development, the terms "layers" and "tiers" are often used interchangeably, but they have different meanings.

- **Layers**: Virtual separations of different parts of an application.
- **Tiers**: Different parts of an application that are physically separated in the application infrastructure.

# N-Tier architecture

N-tier architecture is an application architecture that is split into multiple tiers. The most common type of N-tier architecture is the 3-tier architecture. In some cases, a 4-tier architecture is used.

## 3-Tier Archictecture

A 3-tier architecture consists of the following three tiers:

- **Presentation Tier**: The client computer or mobile that is used to browse a web application or access APIs. This tier is also known as a thin client because it does not run business logic and only communicates with the application to present data.
- **Application Tier**: The tier that holds the application code or business logic that processes data.
- **Data Tier**: The tier that deals with data storage.

## 4-Tier Architecture

In a 4-tier architecture, a fourth tier is added, called the delivery tier. This tier deals with caching and delivering front-end assets to the client, such as a Content Delivery Network (CDN).

# Benefits of N-Tier Architecture

- Easier to secure and scale the application.
- Fixing problems or adding new features becomes more manageable.
- The application development process becomes more efficient.

# Conclusion

In this video, you learned about the difference between layers and tiers and how to use N-tier architecture to create a 3 or 4-tier architecture for web applications.