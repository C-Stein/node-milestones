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
const db = new Database(':memory:', () => console.log('Database open!'));
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


#### Creating a table



















#### Additional Resources

###### [SQLite Website](https://www.sqlite.org/)
######  [SQLite Tutorial | Language Reference](https://www.tutorialspoint.com/sqlite/index.htm)
##### [sqlite3 API docs](https://github.com/mapbox/node-sqlite3/wiki/API)
