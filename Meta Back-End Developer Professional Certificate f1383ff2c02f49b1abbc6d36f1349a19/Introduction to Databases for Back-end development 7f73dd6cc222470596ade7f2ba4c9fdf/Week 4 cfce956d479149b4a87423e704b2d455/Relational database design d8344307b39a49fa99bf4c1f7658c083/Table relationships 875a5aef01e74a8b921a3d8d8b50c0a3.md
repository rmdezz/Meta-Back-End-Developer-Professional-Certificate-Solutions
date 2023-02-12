# Table relationships

Table relationships refer to the connections between different tables in a database. These relationships can be defined using primary and foreign keys. The type of relationship between tables can be one-to-many, one-to-one, or many-to-many.

# One to many relationships

Consider a company that has a "Employees" table and a "Departments" table. Each employee can only belong to one department, but each department can have multiple employees.

```sql
Employees table:
+------------+----------+--------------+
| EmployeeID |  Name    | DepartmentID |
+------------+----------+--------------+
| 1          | John Doe | 1            |
| 2          | Jane Doe | 2            |
| 3          | Joe Smith| 1            |
+------------+----------+--------------+

Departments table:
+--------------+----------------+
| DepartmentID | DepartmentName |
+--------------+----------------+
| 1            | IT             |
| 2            | HR             |
| 3            | Marketing      |
+--------------+----------------+
```

Here, the **`DepartmentID`** column in the "Employees" table is a foreign key that references the primary key **`DepartmentID`** in the "Departments" table. This forms a one-to-many relationship, where one department can have multiple employees, but each employee can only belong to one department.

# One to one relationship

Consider a personal library system where a user has a "Books" table and a "BookDetails" table. Each book can only have one set of details and each set of details can only belong to one book.

```sql
Books table:
+------------+------------------------+
| BookID     | Title                  |
+------------+------------------------+
| 1          | The Lord of the Rings  |
| 2          | Harry Potter           |
| 3          | The Catcher in the Rye |
+------------+------------------------+

BookDetails table:
+------------+---------------+----------------+----------------+
| BookID     | ISBN          | Author         | PublicationDate|
+------------+---------------+----------------+----------------+
| 1          | 1234567890123 | J.R.R. Tolkien | 1954-07-29     |
| 2          | 9876543219876 | J.K. Rowling   | 1997-07-26     |
| 3          | 4567890123456 | J.D. Salinger  | 1951-07-16     |
+------------+---------------+----------------+----------------+
```

Here, the **`BookID`** column in the "BookDetails" table is a foreign key that references the primary key **`BookID`** in the "Books" table. This forms a one-to-one relationship, where each book has one set of details and each set of details can only belong to one book.

# Many to many relationship

A real-world example of this relationship is a university's registration system, where students can register for multiple classes and each class can have multiple students registered.

```sql
Student Table
+-------------+---------+---------+
| Student ID  | Name    | Major   |
+-------------+---------+---------+
| 1           | John    | Computer Science |
| 2           | Sarah   | Mathematics |
| 3           | Michael | Biology |
+-------------+---------+---------+

Course Table
+-------------+-----------------------+------------------+
| Course ID   | Course Name           | Department       |
+-------------+-----------------------+------------------+
| 1           | Calculus I            | Mathematics      |
| 2           | Computer Programming  | Computer Science |
| 3           | Anatomy and Physiology| Biology          |
+-------------+-----------------------+------------------+

Student_Course Table (Junction table)
+-------------+-------------+
| Student ID  | Course ID   |
+-------------+-------------+
| 1           | 2           |
| 2           | 1           |
| 3           | 2           |
| 2           | 3           |
+-------------+-------------+
```

In this example, you can see how the Student_Course table serves as a junction table connecting the Student table and Course table, creating the many-to-many relationship. Each student can be enrolled in multiple courses and each course can have multiple students.