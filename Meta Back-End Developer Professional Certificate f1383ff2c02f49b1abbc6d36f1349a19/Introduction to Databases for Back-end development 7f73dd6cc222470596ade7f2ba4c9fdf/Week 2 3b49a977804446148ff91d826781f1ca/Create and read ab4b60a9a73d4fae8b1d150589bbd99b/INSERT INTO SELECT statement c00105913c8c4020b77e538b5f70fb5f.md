# INSERT INTO SELECT statement

The INSERT INTO SELECT statement is used to query data from one table and insert it into another table. In order to do this, you will use the SQL syntax that consists of the INSERT INTO clause, the SELECT keyword, and the FROM keyword.

# Example

For example, let's say we have a source table called "players" that contains information about soccer players and a target table called "countries" that needs to be populated with the countries where the players are from. The "players" table might look something like this:

```sql
+----+-------+----------+
| ID | Name  | Country  |
+----+-------+----------+
| 1  | John  | USA      |
| 2  | Peter | Brazil   |
| 3  | Mark  | Spain    |
+----+-------+----------+
```

| id | name | country_code |
| --- | --- | --- |
| 1 | John Smith | US |
| 2 | Jane Doe | CA |
| 3 | Robert Lee | CN |

And the "countries" table would look like this (yes, it’s empty for now):

```sql
+----+----------+
| ID | Country  |
+----+----------+
|    |          |
+----+----------+
```

To insert the data from the "players" table into the "countries" table, we would use the following SQL syntax:

```sql
INSERT INTO countries (Country)
SELECT Country FROM players;
```

This statement is saying that we want to insert the data from the `"Country"` column of the `"players"` table into the `"Country"` column of the `"countries"` table. By running this statement, the `"countries"` table will now be populated with the data from the `"players"` table:

```sql
+----+----------+
| ID | Country  |
+----+----------+
| 1  | USA      |
| 2  | Brazil   |
| 3  | Spain    |
+----+----------+
```

It's important to note that the columns you want to insert the data into and select the data from **must have the same datatype**, otherwise an error message will appear. 

Also, it's important to note that **the number of columns you want to insert data into must match the number of columns you are selecting data from**, otherwise, an error message will appear. For example, if you want to insert data into 3 columns in your target table, you must select data from 3 columns in your source table.

## Where clause (filter data)

It's also worth mentioning that the `INSERT INTO SELECT` statement can also be used with a `WHERE` clause, which allows you **to filter the data that's being inserted.** For example, you can insert data from the players table only for players from a specific country. The syntax for this would look like this:

```sql
INSERT INTO countries (code, name, continent)
SELECT country, name, continent
FROM players
WHERE country = 'USA';
```

## Set clause (modify data)

Another feature that can be used in combination with the `INSERT INTO SELECT` statement is the `"SET"` clause. This allows you to **modify the data that's being inserted before it is inserted into the target table.** For example, you can use the SET clause to change the name of a column in the source table before it is inserted into the target table. The syntax for this would look like this:

```sql
INSERT INTO countries (code, name, continent)
SELECT country AS code, name, continent
FROM players
SET name = UPPER(name);
```

Overall, the INSERT INTO SELECT statement allows you to query data from a source table and insert it into a target table with great flexibility and ease.