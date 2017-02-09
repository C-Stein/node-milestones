# Introduction to SQL with Music History
Now that you have created a visual diagram of how the tables in Music History relate to each other, let's stay in this database while you learn how to query it to get back exactly the data you need.

## Setup

Create a file called `queries.sql`

> **Note:** The `.sql` extension is common practice for files storing SQL queries

### Installation of SQLite (if needed)

To get started, type the following command to check if you already have SQLite installed.

```bash
$ sqlite3
```

And you should see:

```
SQLite version 3.7.15.2 2014-08-15 11:53:05
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite>
```

If you do not see above result, then it means you do not have SQLite installed on your machine. Follow the appropriate instructions below.

#### For Windows

Go to [SQLite Download page](http://www.sqlite.org/download.html) and download the precompiled binaries for your machine. You will need to download `sqlite-shell-win32-*.zip` and `sqlite-dll-win32-*.zip` zipped files.

Create a folder `C:\sqlite` and unzip the files in this folder which will give you `sqlite3.def`, `sqlite3.dll` and `sqlite3.exe` files.

Add `C:\sqlite` to your [PATH environment variable](http://dustindavis.me/update-windows-path-without-rebooting/) and finally go to the command prompt and issue `sqlite3` command.

#### For Mac

First, try to install via Homebrew:

```
brew install sqlite3
```

If that doesn't work, download the package from above. After downloading the files, follow these steps:

```
$tar -xvzf sqlite-autoconf-3071502.tar.gz
$cd sqlite-autoconf-3071502
$./configure --prefix=/usr/local
$make
$make install
```

#### Talking to a Database

###### SQL Statements
 * SQL keywords are written in CAPS
 * Basic Structure of a SQL statement:
  `SELECT ______   
  FROM ______
  JOIN ______ ON ______
  WHERE ______`

* Example:  `SELECT * FROM employees WHERE name LIKE ‘b%’`
   * LIKE means “matches a pattern” and % means “starts with” (wildcard).

* Example 2: `SELECT products.id, products.name FROM order_details JOIN products ON  order_details.product_id = products.id WHERE order_details.order_id = 10250`

###### Joins
* http://blog.codinghorror.com/a-visual-explanation-of-sql-joins/
* With a join, you must specify how the table is joined using ON. Otherwise, you will get all the combinations possible of one table row matched with another table row.
  * **Inner Join** matches one table with another table row for row. If one row doesn’t have its pair on another table, it will be excluded. It will only show matching row pairs.
  * **Outer Join** matches two tables row for row but includes rows that are not paired up, aka rows that have a pair with a null in the other table.
  
## Instructions

1. Open up the database file in the *DB Browser for SQLite* application to see it
1. Copy and paste the queries below into your `queries.sql` file and comment them out. Then you can write a query for each requrement and refer back to them later as a resource
1. When you have written a query, paste it into DB Browser and test it by clicking the tab labeled "Execute SQL"

For each of the following exercises, provide the appropriate query. Everything from class and the [Sqlite](http://www.sqlite.org/) documentation for SQL [keywords](https://www.sqlite.org/lang.html) and [functions](https://www.sqlite.org/lang_corefunc.html) is fair game. Note that 

1. Query all of the entries in the `Genre` table
1. Using the `INSERT` statement, add one of your favorite artists to the `Artist` table.
1. Using the `INSERT` statement, add one, or more, albums by your artist to the `Album` table.
1. Using the `INSERT` statement, add some songs that are on that album to the `Song` table.
1. Write a `SELECT` query that provides the song titles, album title, and artist name for all of the data you just entered in. Use the [`LEFT JOIN`](https://www.tutorialspoint.com/sql/sql-using-joins.htm) keyword sequence to connect the tables, and the `WHERE` keyword to filter the results to the album and artist you added. Here is some more info on [joins](http://www.dofactory.com/sql/join) that might help.
    > **Reminder:** Direction of join matters. Try the following statements and see the difference in results.

    ```
    SELECT a.Title, s.Title FROM Album a LEFT JOIN Song s ON s.AlbumId = a.AlbumId;
    SELECT a.Title, s.Title FROM Song s LEFT JOIN Album a ON s.AlbumId = a.AlbumId;
    ```
1. Write a `SELECT` statement to display how many songs exist for each album. You'll need to use the `COUNT()` function and the `GROUP BY` keyword sequence.
1. Write a `SELECT` statement to display how many songs exist for each artist. You'll need to use the `COUNT()` function and the `GROUP BY` keyword sequence.
1. Write a `SELECT` statement to display how many songs exist for each genre. You'll need to use the `COUNT()` function and the `GROUP BY` keyword sequence.
1. Using `MAX()` function, write a select statement to find the album with the longest duration. The result should display the album title and the duration.
1. Using `MAX()` function, write a select statement to find the song with the longest duration. The result should display the song title and the duration.
1. Modify the previous query to also display the title of the album.

# Online SQL Tutorial

There are two online tutorials that are very handy tools if you ever want to quickly churn through the basics of the SQL language against a pre-built database.

1. [Basic SQL Course](http://www.sqlcourse.com/intro.html)
2. [Intermediate SQL Course](http://www.sqlcourse2.com/intro2.html)
