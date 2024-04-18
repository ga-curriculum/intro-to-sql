# ![Intro to SQL - Inserting and Selecting Data](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to insert data into a table and query data from a table.

## Inserting Data

We have a database and a table, but it's empty! Using the `INSERT INTO` command, we can add a single or multiple rows to a table. The syntax for the `INSERT INTO` command is as follows:

**`INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...)[, (value1, value2, ...), ...];`**

Let's add some bands to the `bands` table:

```sql
-- Insert a single row
INSERT INTO bands (name, genre) VALUES ('The Beatles', 'Rock');

-- Insert multiple rows
INSERT INTO bands (name, genre) VALUES ('The Rolling Stones', 'Rock'), ('The Who', 'Rock');
```

> 👀 We are not specifying the `id` column when inserting data into the `bands` table. Since the `id` column is a `SERIAL` data type, PostgreSQL will automatically increment the value each time a new row is inserted.

## Selecting Data

Now that we have data in our `bands` table, we can use the `SELECT` command to query the data. The syntax for the `SELECT` command is as follows:

**`SELECT column1, column2, ... FROM table_name;`**

Let's query all the data from the `bands` table:

```sql
SELECT * FROM bands;
```

> 🧠 The `*` is a wildcard character that selects all columns from the table. If you only want to select specific columns, you can replace the `*` with the column names you want to select.

You should see the data you inserted into the `bands` table in the terminal.

Some standard clauses that can be used with the `SELECT` command are:

- `WHERE`: Filters the rows returned based on a condition.
- `ORDER BY`: Sorts the rows returned based on a column.
- `LIMIT`: Limits the number of rows returned.
- `COUNT`: Returns the number of rows returned.

Let's see some of these clauses in action:

```sql
-- Query bands where the genre is 'Rock'
SELECT name FROM bands WHERE genre = 'Rock';

-- Query bands sorted by name in ascending order
SELECT genre FROM bands ORDER BY name ASC;

-- Query the first two bands
SELECT * FROM bands LIMIT 2;

-- Count the number of bands
SELECT COUNT(*) FROM bands;
```

While the `SELECT` command may not seem very powerful at such a small scale, as you work with more extensive databases and more complex queries, you will see the true power of SQL.
