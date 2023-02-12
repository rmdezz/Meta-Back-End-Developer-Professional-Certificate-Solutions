# Database Evolution

# Introduction

The text explains the history of database technology, how it evolved and different types of databases.

# Background

The history of databases begins in the 1960s with the computerization of databases, as computers emerged as a more cost-effective option for organizations and it became easier to shift data storage and databases to computers.

The chronological order of the development of databases:

| 1970s - 1990s | Flat files, hierarchical and network databases |
| --- | --- |
| 1980s - present | Relational databases |
| 1990s - present | Object-oriented, object-relational, web-enabled |

## Flat files

- Flat files databases were used during the 1970s-1990s, it is a type of database system that stores data in a single file or table, they are basically text files, where every line contains one record, and fields either have fixed lengths or are separated by commas, whitespaces and tabs.
- They cannot contain multiple tables, an example of a flat file database would look like this: OrderID, CustomerID, OrderDate separated by commas.

![[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution)](Database%20Evolution%20de72b667dfe84a4f84693630d8dd0980/Untitled.png)

[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution)

## Hierarchical Databases

- Hierarchical database systems that were in use during the same era store data in a hierarchically arranged manner, it represents a one-to-many relationship: all attributes of a specific record are listed under an entity type.
- An example of how data is stored in a hierarchical database is a college students database, where a course can be assigned to only a single student, but a student can take as many courses as they want.

![[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution)](Database%20Evolution%20de72b667dfe84a4f84693630d8dd0980/Untitled%201.png)

[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution)

## Network Databases

- Network databases were introduced by Charles Bachmann, unlike the hierarchical database model, it allows multiple parent and child relationships, in other words, many-to-many relationships.
- A network database has a graph-like structure, and it allows you to represent more complex relationships among data.
- An example of a network database is a teacher-student database, where a teacher can teach multiple courses and a course can have multiple teachers teaching it.

![[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution)](Database%20Evolution%20de72b667dfe84a4f84693630d8dd0980/Untitled%202.png)

[https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution](https://www.coursera.org/learn/intro-to-databases-back-end-development/supplement/cXSl1/database-evolution)

## Relational Databases

- Relational databases were introduced in the 1980s and are still widely used today. They are based on the relational model, which is a mathematical model that defines a set of relations between data.
- In a relational database, data is organized into tables with rows and columns, and relationships between data are established through the use of foreign keys.
- An example of a relational database is a customer-order database, where a customer can have multiple orders and an order can belong to only one customer.

![[https://phoenixnap.com/kb/object-oriented-database](https://phoenixnap.com/kb/object-oriented-database)](Database%20Evolution%20de72b667dfe84a4f84693630d8dd0980/Untitled%203.png)

[https://phoenixnap.com/kb/object-oriented-database](https://phoenixnap.com/kb/object-oriented-database)

## Object-oriented Databases

- Object-oriented databases were introduced in the 1990s and are based on the object-oriented programming model. They allow for the storage of objects and their relationships with other objects.
- An example of an object-oriented database is a game database, where objects such as characters, weapons, and levels are stored and their relationships with each other are established.

![Untitled](Database%20Evolution%20de72b667dfe84a4f84693630d8dd0980/Untitled%204.png)

## Object-relational Databases

- Object-relational databases are a combination of relational and object-oriented databases, they allow for the storage of objects and their relationships with other objects, as well as the use of SQL to query the data.
- An example of an object-relational database is an e-commerce database, where products and their relationships with categories and manufacturers are stored.

## Web-enabled Databases

- Web-enabled databases are databases that are designed to be accessed and manipulated through the internet. They allow for real-time access to data and make it easy for users to interact with the database through web applications.
- An example of a web-enabled database is a social media platform, where users can create accounts, post content, and interact with other users through the website.

# NoSQL Databases

- NoSQL databases are a type of database that was introduced as a response to the need for faster speed and the processing of unstructured data.
- NoSQL databases are preferred over relational databases because of their speed and flexibility in storing data. They do not store data in relations or tables that belong to a strict structure.
- Data can be stored in an ad-hoc manner and they allow to store and process high volumes of different kinds of data.
- NoSQL databases are capable of processing unstructured big data that's generated by social media, IoT and others. Therefore, social platforms like Twitter, LinkedIn, Facebook, and Google for example makes use of NoSQL databases.

## Advantages of NoSQL Databases

- Higher scalability
- Distributed
- Lower costs
- A flexible schema
- Can process unstructured and semi-structured data
- Has no complex relationships

## Different types of NoSQL databases include

- Document databases: store data in documents similar to JSON (JavaScript Object Notation) objects. Each document contains pairs of fields and values.
- Key-value databases: are a simpler type of database where each item contains keys and values.
- Wide-column databases: store data in tables, rows, and dynamic columns.
- Graph databases: store data in nodes and edges. Nodes typically store information about people, places, and things, while edges store information about the relationships between the nodes.

![Untitled](Database%20Evolution%20de72b667dfe84a4f84693630d8dd0980/Untitled%205.png)

## Example

An example of how NoSQL databases can be useful is in the case of a retail store:

- A retail store can use a NoSQL database to store data on customer orders, product inventory, and sales. This data is unstructured, and a NoSQL database would allow the retail store to easily store and process this data. Additionally, a NoSQL database would allow the retail store to easily scale its database as its customer base grows, making it a more cost-effective solution.

# Conclusion

- In conclusion, database technology has evolved over time to meet the changing needs of organizations and the growing amount of data. Different types of databases have been developed to handle different types of data and relationships, and NoSQL databases have emerged as a popular solution for handling unstructured data and for providing higher scalability and flexibility.
- As more and more data is generated by the Internet, social media, and IoT, the need for efficient and flexible databases will continue to be a crucial aspect of managing and utilizing this data.
- It is important for organizations to stay informed about the latest developments in database technology and to choose the right type of database for their specific needs in order to effectively manage and make use of the data they collect.