# String data types

# Introduction

Relational databases use tables to store data in the form of columns and rows. One important aspect of designing tables is determining the data type of each column, so that the database management system (DBMS) can interpret the values stored in the column correctly. In this case, we are going to explore the string data type and its variations in MySQL, a widely used DBMS.

# String data type

A string data type is used to store data that contains a mix of character types, such as alphabet characters, numeric characters, and special characters. It is a generic term used for different string data types in the database. The most used string data types are CHAR and VARCHAR.

## CHAR data type

The CHAR data type is used to hold characters of a fixed length. It cannot be changed after declaration. The length of the characters is predetermined. For example, CHAR(50) means that a column can only hold 50 characters of space in each field. It is best used when you have a predefined size of characters that you want to maintain. In SQL, you would define a column as CHAR(50) to set a maximum length of 50 characters.

## VARCHAR data type

The VARCHAR data type works similarly to CHAR, but it is a variable length. This means that the length can be changed and it's not fixed. It is often used when you're not sure how many characters might be inserted in the column field. You can type VARCHAR(50) in SQL to allow for any input up to a maximum of 50 characters. It is often used for columns with varying lengths of data.

## Example

| Student Name | Username | Password | Email Address |
| --- | --- | --- | --- |
| Mark | Mark123 | 123456 | mark1@email.com |
| Alex | Alex123 | 123455 | alex1@email.com |

In the above example table, the "Student name" column would use the VARCHAR data type, since student names can vary in length. The "username" column would use CHAR, since the maximum length is predefined.

# Other comon data types

In MySQL, there are several different types of string data types that are commonly used to store text data.

## TINYTEXT

One of these is TINYTEXT, which is used to define columns that require less than 255 characters, such as short paragraphs. 

## TEXT

In MySQL, TINYTEXT, TEXT, MEDIUMTEXT, and LONGTEXT are all commonly used examples of the string data type. Each of these data types has a specific use case and maximum character limit.

- **TINYTEXT**: used for columns that require less than 255 characters, such as short paragraphs or comments.
- **TEXT:** used for columns of less than 65,000 characters, such as an article or a product description.
- **MEDIUMTEXT:** used for columns of up to 16.7 million characters, such as a book or a large document.
- **LONGTEXT:** used for columns that can store up to 4 gigabytes of text data, such as a large collection of research papers.

It's worth noting that when declaring these data types in MySQL, you don't have to specify the maximum number of characters in the parentheses. 

For example, you can use 'TINYTEXT' or 'TEXT' to indicate this data type, you don't have to use 'TINYTEXT(100)' or 'TEXT(100)'.

The values in parentheses, such as TINYTEXT(100) or TEXT(100), indicate the maximum length of characters that the column can store. 

So while TINYTEXT is intended for columns that require less than 255 characters and TEXT is intended for columns that require less than 65,000 characters, you can still use TINYTEXT(100) or TEXT(100) to indicate a maximum length of 100 characters for those specific columns.

# Conclusion

In summary, you learned about the different variations of string data types in MySQL and how to use them to ensure data integrity in a table by allowing only valid values. The CHAR data type is used for fixed length characters and VARCHAR is used for variable length characters. The example table provided demonstrates how each data type could be used in a real-world scenario, by using student information as an example.