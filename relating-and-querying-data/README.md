# ![[tktk Module Name] - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to create a database and tables to store related data.

## One to Many Relationships

We currently have a `bands` table that stores information about different bands. These bands can have many musicians. This relationship is known as a **one-to-many** relationship. We can think through this relationship as:

tktk - Hunter can you take that diagram you made for the `bands` table and add a new table called `musicians` that is connected to the `bands` table with the erd one to many connector line

**A _band_ and many _musicians_, and** <br>
**A _musician_ belongs to a _band_**

To represent this relationship in our database, we must create a new table called `musicians` that will store information about different musicians. The `musicians` table will have a foreign key referencing the `bands` table.

We will want to follow this structure for our `musicians` table.

| Column Name | Data Type | Constraints |
|-------------|-----------|-------------|
| id          | SERIAL    | PRIMARY KEY |
| band_id     | INTEGER   | REFERENCES bands(id) |
| name        | VARCHAR   | NOT NULL    |
| age         | INTEGER   | NOT NULL    |
| sings       | BOOLEAN   |             |
| dances      | BOOLEAN   |             |

To create the `musicians` table, use the `CREATE TABLE` command:

```sql
CREATE TABLE musicians (
  id SERIAL PRIMARY KEY,
  band_id INTEGER REFERENCES bands(id),
  name VARCHAR NOT NULL,
  age INTEGER NOT NULL,
  sings BOOLEAN,
  dances BOOLEAN
);
```

Let's insert the musicians for the bands we have in the `bands` table:

```sql
-- Insert musicians for The Beatles
INSERT INTO musicians (band_id, name, age, sings, dances) VALUES (1, 'John Lennon', 40, null, FALSE), (1, 'Paul McCartney', 39, TRUE, FALSE), (1, 'George Harrison', 38, TRUE, null), (1, 'Ringo Starr', 41, FALSE, TRUE);

-- Insert musicians for The Rolling Stones
INSERT INTO musicians (band_id, name, age, sings, dances) VALUES (2, 'Mick Jagger', 38, TRUE, null), (2, 'Keith Richards', 39, TRUE, FALSE), (2, 'Charlie Watts', 40, null, FALSE), (2, 'Ronnie Wood', 41, TRUE, TRUE);

-- Insert musicians for The Who
INSERT INTO musicians (band_id, name, age, sings, dances) VALUES (3, 'Roger Daltrey', 38, TRUE, TRUE), (3, 'Pete Townshend', 39, null, FALSE), (3, 'John Entwistle', 40, TRUE, FALSE), (3, 'Keith Moon', 41, null, TRUE);
```

> 🧠 The `null` value represents unknown or missing data. Since the `sings` and `dances` columns are `BOOLEAN` data types without any constraints, we can represent the data using `TRUE`, `FALSE`, or `null`.

## Querying Data

We have seen how to `SELECT` data from a single table and some common clauses that can be used with the `SELECT` command. Let's dive deeper into querying data and the power of the `WHERE` clause.

The `WHERE` clause filters the rows returned based on a condition. The syntax for the `WHERE` clause is as follows:

**`SELECT column1, column2, ... FROM table_name WHERE condition;`**

Let's query the musicians that sing:

```sql
SELECT name FROM musicians WHERE sings = TRUE;
```

You should see the musicians that sing displayed in the terminal.

Some standard comparison operators that can be used in the `WHERE` clause are:

- `=`: Equal to
- `<>` or `!=`: Not equal to
- `>`: Greater than
- `<`: Less than
- `>=`: Greater than or equal to
- `<=`: Less than or equal to
- `BETWEEN`: Between an inclusive range
- `LIKE`: Search for a pattern
- `IN`: Matches any of a list of values
- `IS NULL`: Checks for `NULL` values
- `AND`: Combines multiple conditions
- `OR`: Returns rows that meet either condition
- `NOT`: Negates a condition

Let's see some of these operators in action:

```sql
-- Query musicians who are older than 40
SELECT name FROM musicians WHERE age > 40;

-- Query musicians that are younger than or equal to 40
SELECT name FROM musicians WHERE age <= 40;

-- Query musicians that are between the ages of 38 and 40
SELECT name FROM musicians WHERE age BETWEEN 38 AND 40;

-- Query musicians that have a name that starts with 'J'
SELECT name FROM musicians WHERE name LIKE 'J%';

-- Query musicians that are in The Beatles or The Rolling Stones
SELECT name FROM musicians WHERE band_id IN (1, 2);

-- Query musicians that do not sing
SELECT name FROM musicians WHERE sings IS NULL;

-- Query musicians who are older than 40 and do dance
SELECT name FROM musicians WHERE age > 40 AND dances = TRUE;

-- Query musicians that are younger than or equal to 40 or sing
SELECT name FROM musicians WHERE age <= 40 OR sings = TRUE;

-- Query musicians that are not older than 40
SELECT name FROM musicians WHERE NOT age > 40;
```

The `WHERE` clause is a powerful tool that allows you to filter the data returned based on a condition. To create complex queries, you can combine multiple conditions using the `AND` OR`, and `NOT` operators.

## Querying Related Data

Now that we have data in both the `bands` and `musicians` tables, we can query related data using the `JOIN` command. The `JOIN` command combines rows from two or more tables based on a related column between them. The syntax for the `JOIN` command is as follows:

**`SELECT table1.column1, table2.column2, ... FROM table1 JOIN table2 ON table1.column = table2.column;`**

Let's query the musicians and the bands they belong to:

```sql
SELECT bands.name AS band, musicians.name AS musician
FROM bands
JOIN musicians ON bands.id = musicians.band_id;
```

You should see the musicians and the bands they belong to displayed in the terminal.

The `JOIN` command is a powerful tool that combines related data from multiple tables. You can use different types of joins, such as:

- `INNER JOIN`: Returns rows when there is a match in both tables
- `LEFT JOIN` or `LEFT OUTER JOIN`: Returns all rows from the left table and the matched rows from the right table
- `RIGHT JOIN` or `RIGHT OUTER JOIN`: Returns all rows from the right table and the matched rows from the left table
- `FULL JOIN` or `FULL OUTER JOIN`: Returns rows when there is a match in one of the tables
