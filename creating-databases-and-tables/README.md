# ![[tktk Module Name] - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to create a database and a table to store data.

## Creating a Database

During this lesson, we will use the PostgreSQL command-line tool. Before proceeding, make sure to follow the [Setup](../setup/README.md) instructions.

Now we know a little more about SQL and relational databases, let's create a database to store our data. We will start with a database called `music` with a table called `bands`.

tktk - Hunter can you add a diagram here showing the relationship between the database and the table? Like a large box labeled 'music' with a smaller box inside labeled 'bands'.

Once in the PostgreSQL command line tool, you can create a new database using the `CREATE DATABASE` command. Let's create a database called `music`:

```sql
CREATE DATABASE music; -- Remember the semicolon!
```

Using the `\l`, you can list all the databases in your PostgreSQL server. You should see the `music` database listed.

> 👀 Use `q` to exit the list view. Comments in SQL begin with `--`.

Before creating a table, we must connect to the `music` database. You can do this using the `\c` command:

```sql
\c music -- Connect to the music database
```

You should see the prompt change to `music=#` indicating that you are now connected to the `music` database.

## Creating a Table

Now that we have a database let's create a table to store our data. We will make a table called `bands` to store information about different bands.

We will want to follow this structure for our `bands` table.

| Column Name | Data Type | Constraints |
|-------------|-----------|-------------|
| id          | SERIAL    | PRIMARY KEY |
| name        | VARCHAR   | NOT NULL    |
| genre       | VARCHAR   |             |


To create the `bands` table, use the `CREATE TABLE` command:

```sql
CREATE TABLE bands (
  id SERIAL PRIMARY KEY,
  name VARCHAR NOT NULL,
  genre VARCHAR
);
```

> 🧠 `SERIAL` is a PostgreSQL data type that automatically increments the column's value each time a new row is inserted. This is useful for creating unique identifiers for each row in the table.

To verify that the `bands` table was created successfully, you can use the `\dt` command to list all the tables in the `music` database. You should see the `bands` table listed.
