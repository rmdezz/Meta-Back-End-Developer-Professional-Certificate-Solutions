# What are tables in databases?

# Introduction

SQL is a powerful tool for interacting with databases, but it's important to have a solid understanding of how databases are structured and organized in order to use it effectively. 

One of the key concepts to understand is the structure of a database table.

# Tables

A table is made up of rows and columns, which hold data and is stored in a database that holds multiple tables. These tables are known as relations, as they all relate to one another. 

A table is also known as an entity and an object in object oriented databases (OOD).

![[https://www.researchgate.net/publication/332816170/figure/fig2/AS:843258271916032@1578059847039/A-database-with-three-tables.png](https://www.researchgate.net/publication/332816170/figure/fig2/AS:843258271916032@1578059847039/A-database-with-three-tables.png)](What%20are%20tables%20in%20databases%20e3c33591f28c4e84a9b0d9a6bfb1ef46/Untitled.png)

[https://www.researchgate.net/publication/332816170/figure/fig2/AS:843258271916032@1578059847039/A-database-with-three-tables.png](https://www.researchgate.net/publication/332816170/figure/fig2/AS:843258271916032@1578059847039/A-database-with-three-tables.png)

# Columns

Each column in a table is also called a field or attribute, and has a unique name and data type. For example, if you have a table that contains data on employees in a company, the table organizes the data in columns such as ID and role, and each column can hold different types of data like numeric or string.

# Data Types

It's important to understand the data types that are supported by the specific database system you are using.  For example, different data types may be supported by MySQL, SQL Server, or Access. Generally, all database systems support string data types for storing characters and strings of characters, numeric data types to store exact or whole numbers and approximate numbers, date and time data types to store information on date and time, and binary data types to store images, files, and other information.

![[https://blog-codeminer42.s3.sa-east-1.amazonaws.com/wp-content/uploads/2022/09/18234449/sql-data-types-1.png](https://blog-codeminer42.s3.sa-east-1.amazonaws.com/wp-content/uploads/2022/09/18234449/sql-data-types-1.png)](What%20are%20tables%20in%20databases%20e3c33591f28c4e84a9b0d9a6bfb1ef46/Untitled%201.png)

[https://blog-codeminer42.s3.sa-east-1.amazonaws.com/wp-content/uploads/2022/09/18234449/sql-data-types-1.png](https://blog-codeminer42.s3.sa-east-1.amazonaws.com/wp-content/uploads/2022/09/18234449/sql-data-types-1.png)

# Domains

Another important concept related to tables is domains. A domain is the set of legal values that can be assigned to an attribute, which means making sure that the values of fields are well defined. For example, you can only place numbers in a numerical domain and you can only place characters or strings of characters in a string domain. Each of these domains must include length values and other relevant rules that define its function.

# Primary Key

- Each row or record in a table is also uniquely identified by what's known as a primary key. A column in the table that has unique values will become the primary key of the table.
- An employee table, for example, the ID column is the primary key as each ID is unique. This is because the other columns could contain repeating values for example, two employees may share the same name or role. It's also possible for a primary key to be a combination of columns. If a single column alone doesn't possess unique values.

![[https://prepinsta.com/wp-content/uploads/2021/04/Primary-Key.webp](https://prepinsta.com/wp-content/uploads/2021/04/Primary-Key.webp)](What%20are%20tables%20in%20databases%20e3c33591f28c4e84a9b0d9a6bfb1ef46/Untitled%202.png)

[https://prepinsta.com/wp-content/uploads/2021/04/Primary-Key.webp](https://prepinsta.com/wp-content/uploads/2021/04/Primary-Key.webp)

# Conclusion

- Overall, understanding the structure and organization of databases is crucial for effectively using SQL and working with databases. The concepts of tables, columns, data types, domains, and primary keys are key to this understanding. You should now be familiar with what a database is and be able to explain how it is structured. You should also be able to explain key concepts such as columns, rows, and keys.
- In short, tables are the basic building blocks of a database, where data is organized in a structured way. Each table is made up of rows and columns, with each column having a unique name and data type.
- Data types define the type of value a column can hold and can vary depending on the database system being used.
- Domains are the set of legal values that can be assigned to an attribute, helping to ensure that the values of fields are well defined.
- Finally, primary keys are used to uniquely identify each row in a table, and can be a single column or a combination of columns.

Overall, understanding these concepts is essential for working with databases and using SQL effectively.