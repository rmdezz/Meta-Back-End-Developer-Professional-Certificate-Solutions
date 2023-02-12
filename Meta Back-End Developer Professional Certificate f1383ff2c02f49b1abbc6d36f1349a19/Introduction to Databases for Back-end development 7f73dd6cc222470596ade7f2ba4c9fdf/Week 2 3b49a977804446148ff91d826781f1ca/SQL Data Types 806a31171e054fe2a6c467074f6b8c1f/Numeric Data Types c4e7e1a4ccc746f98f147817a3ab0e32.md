# Numeric Data Types

# Introduction

When working with relational databases, it is important to understand the concept of data types. Data types are used to determine what kind of data is accepted by each field in a table, ensuring that values are stored in the correct format and preventing errors. In this reading, we will focus on numeric data types, which are used for storing numerical values in a database.

# Types

There are two main types of numeric data types: integer and decimal.

- Integer data types, such as TINYINT and INT, are used for storing whole numbers.
- Decimal data types are used for storing numbers with a fractional value.

> For example, in an online store's database, the product quantity column would be defined as an integer data type, while the total price column would be defined as a decimal data type.
> 
- It is important to note that different types of integer and decimal data types exist, each with different minimum and maximum value ranges.

> For example, in MySQL, TINYINT is used for small integer numbers, with a maximum value of 255, while INT can store much larger numbers, with a maximum value of over four billion. These data types can also be configured to accept only positive values, increasing the maximum value they can store.
> 

# Conclusion

To sum up, understanding the concept of data types and how they are used in relational databases is crucial for storing data in the correct format and preventing errors. You should now be able to explain numeric data types, differentiate between integer and decimal data types, and understand the different types of integer and decimal data types, their minimum and maximum value ranges, and how to configure them.