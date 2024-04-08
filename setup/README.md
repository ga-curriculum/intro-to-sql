# ![[tktk Module Name] - Setup](./assets/hero.png)

## Setup

In this lesson, you will use your Terminal application to create and interact with a PostgreSQL database. You will use the `psql` command line tool to interact with the database. Open your Terminal application and use the command `psql` to start the PostgreSQL command line tool:

```bash
psql
```

You should see a prompt that looks like this:

```bash
psql (14.9 (Homebrew))
Type "help" for help.

username=#
```

> The version number, `(14.9 (Homebrew))`, may be different on your machine. You are in the PostgreSQL command line tool if you can see your username followed by a `#`.

To close the PostgreSQL command line tool, type `\q` and press `Enter`:

```bash
\q
```

## Optional Setup Instructions

If you would like to take notes or save SQL commands for later, pen your Terminal application and navigate to your **`~/code/ga/lectures`** directory:

```bash
cd ~/code/ga/lectures
```

Make a new directory called **`intro-to-sql`**, then enter this directory:

```bash
mkdir intro-to-sql
cd intro-to-sql
```

To create a new file called **`notes.md`**, use the `touch` command:

```bash
touch notes.md
```

To create a SQL file called **`queries.sql`**, use the `touch` command:

```bash
touch queries.sql
```

Open the contents of the directory in VSCode:

```bash
code .
```