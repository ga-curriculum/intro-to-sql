# ![Intro to SQL - Concepts](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to explain the concepts of databases and SQL.

## What is a Database?

The vast majority of applications manipulate and display data.

Early on, our programs held data in "memory" using data structures such as arrays and objects. However, when the app was exited, any changes to the data were lost - databases avoid this...

Simply put, **a database provides permanent storage for data**.

### Different Types of Databases

[This site](https://db-engines.com/en/ranking) ranks databases according to their popularity.

As you can see, there are several different types of databases and several "brands" within each type.

Most database technologies can be broken down into two main categories:

- Relational databases
- NoSQL databases

Relational databases are by far the most popular type of database technology. Conceived by [E.F. Codd](https://en.wikipedia.org/wiki/Edgar_F._Codd) while working for IBM in 1970.

We'll use [PostgreSQL](https://www.postgresql.org/), which is arguably the best open-source relational database management system (RDBMS) available.

## Anatomy of a Relational Database

### Schema

The structure of a particular database is defined by its **schema**.

Schemas define the databases:

- Tables, including the number and data type of each column
- Indexes for efficient access to data
- Constraints (rules, such as whether a field can be null or not)

### Tables

The primary container for data in a relational database is a **table**:

tktk - Hunter this is taken from Jim's content, idk if we want to change this on over to one of your wonderful graphics or not.
<img src="https://i.imgur.com/uL3fvU4.png">

As you can see, database tables look much like spreadsheets since they consist of columns and rows.

A table in a relational database holds data for a particular _data resource_, for example, **customers**, **orders**, **reviews**, etc.

TABLE: **artists**

| id (PK) | name           | nationality |
| ------- | -------------- | ----------- |
| 1       | Prince         | American    |
| 2       | Sir Elton John | British     |

TABLE: **songs**

| id (PK) | name                | year_released | artist_id (FK) |
| ------- | ------------------- | ------------- | -------------- |
| 1       | Tiny Dancer         | 1971          | 2              |
| 2       | Little Red Corvette | 1982          | 1              |
| 3       | Raspberry Beret     | 1985          | 1              |
| 4       | Your Song           | 1970          | 2              |

### Rows (Records)

A row in a table represents a single instance of the data entity.

For example, a particular **artist** is in the **artists** table.

### Columns (Fields)

The columns of a table have a:

- Name
- Data type (all data in a column must be of the same type)
- Optional constraints

The typical naming convention is usually snake_cased and singular.

PostgreSQL has [many data types](https://www.postgresql.org/docs/11/datatype.html) for columns, but common ones include:

- `integer`
- `decimal`
- `varchar` (variable-length strings)
- `text` (same as `varchar`)
- `date` (does not include time)
- `timestamp` (both date and time)
- `boolean`

Typical constraints for a column include:

- `PRIMARY KEY`: column, or group of columns, uniquely identify a row
- `REFERENCES` (Foreign Key): value in a column must match the primary key in another table
- `NOT NULL`: column must have a value; it cannot be empty (null)
- `UNIQUE`: data in this column must be unique among all rows in the table

### Primary Keys (PK) and Foreign Keys (FK)

The field (or fields) that uniquely identify each row in the table are known as that table's **primary key (PK)**.

Since only one type of data entity can be held in a single table, related data, for example, the **songs** for an **artist**, are stored in separate tables and "linked" via what is known as a **foreign key (FK)**.

## Structured Query Language (SQL)

### What is SQL?

**SQL (Structured Query Language)**, also pronounced "sequel," is a programming language for CRUD data stored in a relational database.

SQL syntax is similar to that of the English language.

Although SQL is fairly standard, it can vary depending on the RDBMS (Relational Database Management System). For example, the _SQLite_ RDBMS implements fewer SQL commands than that of _PostgreSQL_.

For this lesson, we will be using PostgreSQL. Postgres is an open-source RDBMS (relational database management system) created at the University of California, Berkeley. It started being built in 1982.
