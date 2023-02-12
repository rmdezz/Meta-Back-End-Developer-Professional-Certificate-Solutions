# Types of keys in a database table

# Relational Database Model

The relational database model is a way to store data in a structured and organized way, using tables and relationships between them. By understanding the main keys used in tables and the relationships between them, you can better understand how a relational database model works.

# Entities and Relations

The relational database model is based on two main concepts, entities which are defined as tables and relations that connect to related tables. Relationships are established between tables with the use of keys. 

An entity is an object that has attributes that are like columns or fields in a table. In the sports competition example, the league table, teams table and points table are entities.

In order to understand how this model works, it's important to understand the different types of keys that exist in a relational database.

# Attributes

Each table has relevant columns where each column represents an attribute of the table entity. The attributes could be of a simple attribute type that can hold a single value, or they could also have a multi-value attribute that can have multiple values. However, multi-value attributes should be avoided in relational database design.

# Types of keys

In a relational database, there are a range of different types of key attributes, including:

| Key attribute | This is a value used to uniquely identify an individual record of data in a table. |
| --- | --- |
| Candidate key | Any attribute that contains a unique value in each row of the table. |
| Composite key | A key that is composed of two or more attributes to form a unique value in each new role. |
| Primary key | A candidate key that is selected as the main identifier for the table. |
| Alternate key (secondary key) | A candidate key that was not selected to be the primary key. |
| Foreign key | An attribute on the table that references a unique key in another table. |

# Example

To illustrate these concepts, let's consider an example of a staff table in a college. The staff table might include the following columns:

- Staff ID (primary key)
- Staff Name
- Staff title
- Contact number (alternate key)

In this example, the Staff ID column serves as the primary key, as it uniquely identifies each record of data in the table. The contact number column can also serve as an alternate key, as it also contains unique values for each staff member.