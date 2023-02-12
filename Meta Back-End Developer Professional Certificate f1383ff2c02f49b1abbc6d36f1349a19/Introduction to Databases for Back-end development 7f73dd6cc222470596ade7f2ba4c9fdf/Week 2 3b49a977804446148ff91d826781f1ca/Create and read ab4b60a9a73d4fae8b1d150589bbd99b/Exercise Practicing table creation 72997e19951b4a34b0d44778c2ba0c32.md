# Exercise: Practicing table creation

# **Goal**

In this exercise, you will learn how to practice table creation in a database from scratch. The objective of the exercise is to build a table in a database for the given scenario. You’ll then review the solution to check and compare your design and implementation of the table.

# **Scenario**

Mr. Erik Anderson has created a new football club for kids under 16 years old. He needs to create a table to store the players’ basic personal data including identity number, name and age.

# **Instructions**

Please attempt the tasks below before you continue, so you can check and compare your answers with the solution.

Task 1: Create a database called football club.

Task 2: Create a table to store the data as follows:

- Identify a suitable table name to store the players’ personal data.
- Identify the table attributes and data types.
- Write a SQL statement to create the table.

# Solution

### Task 1: Create a database called football club

```sql
CREATE DATABASE football_club;
USE football_club;
```

### Task 2: Create a table that satisfies the requirements

```sql
CREATE TABLE players (player_id INT, player_name varchar(100), age INT, nationality varchar(70));
```

# Additional task

Mr. Anderson wants to create another table to record information about the games the team will play, including the gameID, the score of each game and the dates they’re played on. Your task is to create this table for the football club.

### Solution

```sql
CREATE TABLE games (game_id int, game_date date, score int);
```