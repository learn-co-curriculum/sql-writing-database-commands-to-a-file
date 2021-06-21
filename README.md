# Databases and Text Editors

## Objectives

- Write SQL code in your text editor instead of your command line.
- Learn how to execute SQL code you've written in your text editor against a
  database you've created.

## Writing SQL in a Text Editor

Up until now, we've been executing our SQL commands directly in the terminal. It
is likely, however, that you will find yourself writing SQL in a file and
executing that file in the context of your database. The more complex our
databases become, the more tables we add and the more advanced the queries we
run against them, the harder it will become to keep track of it all in the
`sqlite3` prompt in our terminal.

SQL is a programming language like any other, so we can write SQL in our text
editor and execute it. This allows us to keep better track of our SQL code,
including the SQL statements that create tables and query data from those
tables.

To write SQL in our text editor and execute that SQL against a specific
database, we'll create files in our text editor that have the `.sql` extension.
These files will contain valid SQL code. Then, we can execute these files
_against our database_ in the command line. We'll take a look at this process
together in the following code along.

## Code Along

### Creating a Database and Table

1 . In the terminal, create a database with the following command:

```sh
sqlite3 pets_database.db
```

**Once you create your database, exit the sqlite prompt with the `.quit` command.**

Open up a text editor and create and save a file `01_create_cats_table.sql`;
make sure the new file is saved in the same directory where you created the
database. In this file, write your create statement:

```sql
CREATE TABLE cats (
  id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER
);
```

2 . Execute that file in the command line. _Before running the command below,
make sure that you've exited the SQLite prompt that you were in earlier when you
created the database._

```sh
sqlite3 pets_database.db < 01_create_cats_table.sql
```

> **Note**: You won't be able to view the `pets_database.db` file directly
> in your text editor. This file is the binary representation of the database.
> You can think of this like a .jpg file. It won't open up in a text editor,
> but it does open up in the image viewer app. It is the same way for .db
> files. They won't open in your editor, but they can be read by the
> appropriate database engine.

**Note:** If running the above command gives you an error that the Cats table
already exists, that means you created a table with that name in a previous
exercise. You can enter into your Pets Database with the `sqlite3 pets_database.db`
command and then remove your old table in the SQLite prompt with:

```sql
DROP TABLE cats;
```

### Confirming Our SQL Execution

Let's confirm that the above execution of the SQL commands in our `.sql` file
worked. To do so:

1 . In your terminal, enter into your Pets Database with the
`sqlite3 pets_database.db` command.

2 . Then run the `.schema` command. You should see the following schema printed
out, confirming that we did, in fact, create our Cats table successfully.

```sql
CREATE TABLE cats (
  id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER
);
```

**Remember to exit out of the `sqlite3` prompt with `.quit`.**

### Operating on our Database from the Text Editor

To carry out any subsequent actions on this database &mdash; adding a column to the
cats table, dropping that table, creating a new table &mdash; we can create new `.sql`
files in the text editor and execute them in the same way as above. Let's give
it a shot.

1 . To add a column to our cats table:

Create a file named `02_add_column_to_cats.sql` and fill it out with:

```sql
ALTER TABLE cats ADD COLUMN breed TEXT;
```

Then, execute the file in your command line:

```sh
sqlite3 pets_database.db < 02_add_column_to_cats.sql
```

2 . Confirm that your execution of the `.sql` file worked by entering into your
database in the terminal with the `sqlite3 pets_database.db` command. Once
there, execute the `.schema` command and you should see that the schema of the
Cats table does include the `breed` column.
