# ![Intro to SQL - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to modify and delete data in a database.

## Modifying or Updating Data

We have seen how to insert data into a table, but what if we need to update existing data? The `UPDATE` command is used to modify existing data in a table. The syntax for the `UPDATE` command is as follows:

**`UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;`**

Let's say we want to update the genre of the band `The Beatles` to `Rock and Roll`. We can use the `UPDATE` command to do this:

```sql
UPDATE bands SET genre = 'Rock and Roll' WHERE name = 'The Beatles';
```

> 🧠 The `WHERE` clause is used to filter the rows that will be updated. If you omit the `WHERE` clause, all rows in the table will be updated.

We can also update multiple columns at once. Let's say we want to update the genre of the band `The Rolling Stones` to `Rock and Roll` and the genre of the band `The Who` to `Rock and Blues`. We can use the `UPDATE` command to do this:

```sql
UPDATE bands SET genre = 'Rock and Roll' WHERE name = 'The Rolling Stones';
UPDATE bands SET genre = 'Rock and Blues' WHERE name = 'The Who';
```

## Deleting Data

The `DELETE` command is used to remove rows from a table. The syntax for the `DELETE` command is as follows:

**`DELETE FROM table_name WHERE condition;`**

Let's say we want to delete the musician `Roger Daltrey` from the `musicians` table. We can use the `DELETE` command to do this:

```sql
DELETE FROM musicians WHERE name = 'Roger Daltrey';
```

## Summary

As much fun as it is to write SQL, most developers only have a few opportunities to do so because they typically use an Object Relational Mapper (ORM) software to automatically write SQL and communicate with the database server.

Regardless, understanding enough SQL to put it on your resume is important!
