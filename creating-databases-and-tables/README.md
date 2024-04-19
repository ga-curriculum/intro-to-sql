# ![Intro to SQL - Creating Databases and Tables](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to create a new database and table with PostgreSQL.

## Creating a Database

During this lesson, we will use the PostgreSQL command-line tool. Before proceeding, make sure to follow the [Setup](../setup/README.md) instructions.

Now that we know a little more about SQL and relational databases, let's create a new database to store some data. We will start with a database called `music` with a table called `bands`.

tktk - Hunter can you add a diagram here showing the relationship between the database and the table? Like a large box labeled 'music' with a smaller box inside labeled 'bands'.

Once in the PostgreSQL command line tool, you can create a new database using the `CREATE DATABASE` command. Let's create a database called `music`:

```sql
CREATE DATABASE music; -- Remember the semicolon!
```

Using the `\l`, you can list all the databases in your PostgreSQL server. You should see the `music` database listed.

> 👀 Use `q` to exit the list view. Comments in SQL begin with `--`.

Before creating a new table, we must connect to the `music` database. You can do this using the `\c` command:

```sql
\c music -- Connect to the music database
```

You should see the prompt change to `music=#` indicating that you are now connected to the `music` database.

## Creating a Table

With our database set up, the next step is to create a table to organize and store specific data. We'll start by creating a table called `bands`, which will hold information about various musical bands.

Our `bands` table will have three columns: `id`, `name`, and `genre`.

| Column Name | Data Type | Constraints | Notes                                                                                                                                                                                   |
| ----------- | --------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | SERIAL    | PRIMARY KEY | A unique identifier for each band. We use the SERIAL data type here, which automatically generates a new, incremental number for each entry, ensuring that each band has a unique ID.   |
| name        | VARCHAR   | NOT NULL    | We've chosen VARCHAR as the data type, which allows us to store strings of varying lengths. The NOT NULL constraint ensures that every band entered into the database must have a name. |
| genre       | VARCHAR   |             | This is also VARCHAR, however, this column has no constraints so it’s optional to fill this in.                                                                                                                       |

To create this table in PostgreSQL, we use the `CREATE TABLE` command.

```sql
CREATE TABLE bands (
  id SERIAL PRIMARY KEY,
  name VARCHAR NOT NULL,
  genre VARCHAR
);
```

> Inside the parentheses, we define the columns and their respective settings, such as data types and constraints.

After creating the table, it's good practice to check if it has been set up correctly. You can list all the tables in your `music` database using the command `\dt`. If the `bands` table has been created successfully, it will appear in the list output by this command.
