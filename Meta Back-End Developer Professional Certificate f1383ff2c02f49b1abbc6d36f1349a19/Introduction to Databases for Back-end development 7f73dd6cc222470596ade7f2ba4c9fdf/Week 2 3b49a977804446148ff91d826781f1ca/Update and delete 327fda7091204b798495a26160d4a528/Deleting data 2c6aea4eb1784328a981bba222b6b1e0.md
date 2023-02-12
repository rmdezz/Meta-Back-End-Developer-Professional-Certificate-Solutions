# Deleting data

When working with databases, there may be instances where you need to delete data from a table. In MySQL, you can use the DELETE statement to remove data from a table.

# Deleting a single record

I'll demonstrate how to delete a single record from a table in a database. I'm using the student table from a college database and deleting the record of a student with the last name of Miller. The student table looks like this:

| ID | First Name | Last Name | Home Address | College Address | Contact Number | Department |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | John | Doe | 123 Main St | 456 College St | 555-555-5555 | Biology |
| 2 | Jane | Smith | 789 Elm St | 123 University | 555-555-5556 | Engineering |
| 3 | Michael | Miller | 456 Oak St | 789 College Ave | 555-555-5557 | Chemistry |

```sql
DELETE FROM student_table
WHERE last_name = 'Miller';
```

I get a confirmation that the record Miller has been deleted from the table. I can then access the student table on the left panel to ensure that the record or instance of Miller has been removed. The student table now looks like this:

| ID | First Name | Last Name | Home Address | College Address | Contact Number | Department |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | John | Doe | 123 Main St | 456 College St | 555-555-5555 | Biology |
| 2 | Jane | Smith | 789 Elm St | 123 University | 555-555-5556 | Engineering |

# Deleting multiple records

Let's explore another example this time by deleting multiple records from the student table. Now I want to delete the records for the two students within the engineering department. 

```sql
DELETE FROM student_table
WHERE department = 'engineering';
```

Before the deletion, the student table would look something like this:

| ID | First Name | Last Name | Home Address | College Address | Contact Number | Department |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | John | Doe | 123 Main St | 321 College St | 555-555-5555 | Engineering |
| 2 | Jane | Smith | 456 Park Ave | 789 University | 555-555-5556 | Engineering |
| 3 | Michael | Johnson | 111 Elm St | 222 College Ave | 555-555-5557 | Math |
| 4 | Lisa | Williams | 333 Oak St | 444 University | 555-555-5558 | English |

After the deletion, the student table would look like this:

| ID | First Name | Last Name | Home Address | College Address | Contact Number | Department |
| --- | --- | --- | --- | --- | --- | --- |
| 3 | Michael | Johnson | 111 Elm St | 222 College Ave | 555-555-5557 | Math |
| 4 | Lisa | Williams | 333 Oak St | 444 University | 555-555-5558 | English |

As you can see, the two records for students in the engineering department have been removed. 

# Important

- It's important to note that when using the DELETE statement, it's crucial to be very careful with the WHERE clause as it specifies the records that will be deleted.
- Not including a WHERE clause or specifying the wrong condition could result in deleting unintended data from the table.
- To help prevent any accidental data loss, it's best to test the DELETE statement on a copy of the table or to use a transaction before the DELETE statement.