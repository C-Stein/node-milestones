# SQLite

SQLite is a software library that implements a self-contained, serverless, zero- configuration, transactional SQL database engine.

What does that mean?
1. SQLite does not require a separate server process or system to operate.
2. Creating a SQLite database instance is as easy as opening a file.
3. The entire database instance exists in a single cross-platform file.


## SQLite3

sqlite3 is an npm module that provides a software interface with a SQLite database. With sqlite3 and NodeJS you have the ability to create tables, drop tables, make inserts, query a SQLite database, and more.


### Creating a SQLite Database

```js
// Require in the Database method from the sqlite3 module
// We will be using the verbose execution mode, which will give us better error messages.
const { Database } = require('sqlite3').verbose();

// Returns a new database object and automatically opens the database
// Database method accepts a callback function for successful connection
const db = new Database(':memory:', () => console.log('Connected!'));
```

#### Creating a database in memory vs. as a file

The below lines of code are both creating and opening a database, but how the database will be saved is the difference.

```js
// Creates an anonymous in-memory database
// Contents will be lost when the database connection closes
const db = new Database(':memory:');

// Creates a database which will be written to a file on disk
// Changes will persist once connection closes
const db = new Database('db/example.sqlite');
```

#### Creating a Table

Now lets create a table with some columns. First we will use `db.run()` to execute a SQLite statement to create a table.

```js
db.run("CREATE TABLE employees (id INT, first TEXT, last TEXT)");
```

The above statement will do the following:
1. Create a table named `employees`
2. Create three columns named `id`, `first`, and `last`
3. Specify the data-type of the value for each column. Even if there is a specified data-type, a value of any data-type can still be stored in the column.
  - Constraints can be passed in to restrict certain data-types
  - eg: `first TEXT NOT NULL` will accept any value not equal to null


#### Simple Insert Statement

Lets insert out first records into the `employees` table.

```js
db.run("INSERT INTO employees (id, first, last) VALUES (0, 'Michael', 'Scott')");
// OUTPUT => { id: 0, first: 'Michael', last: 'Scott' }

db.run("INSERT INTO employees VALUES (1, 'Jim', 'Halpert')");
// OUTPUT => { id: 1, first: 'Jim', last: 'Halpert' }
```

The above statements may look different, but they will both insert a record with `id`, `first`, and `last` values into the table. Omitting the `(id, first, last)` from the first statement will not change the outcome, but make sure that the values (eg: `(0, 'Michael', 'Scott')`) which are passed in are in the **same order as they were defined when the table was created.**

Example:
```
"CREATE TABLE employees (id INT, first TEXT, last TEXT)"

Correct: "INSERT INTO employees VALUES (2, 'Pam', 'Beesly')"

Incorrect: "INSERT INTO employees VALUES ('Beesly', 2, 'Pam')"
```






















#### Additional Resources

###### [SQLite Website](https://www.sqlite.org/)
######  [SQLite Tutorial | Language Reference](https://www.tutorialspoint.com/sqlite/index.htm)
##### [sqlite3 API docs](https://github.com/mapbox/node-sqlite3/wiki/API)
