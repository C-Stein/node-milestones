# SQLite Practice

In this exercise you will create a SQLite database, create tables, insert records to the table, and query the database. We will be using the npm module [sqlite3](https://www.npmjs.com/package/sqlite3).

This exercise is based on the [SQLite Intro Exercise]('./17-SQLite_01.md'), so make sure that you have completed it before attempting this exercise.


## Setup

```
cd workspace/node/exercises
mkdir sqlite101
cd sqlite101
npm install sqlite3 --save
touch sqlite3.js
```

## Instructions

A friend of yours owns a small family business and wants to start moving all of their business records into a database. Using your NodeJS skills, they want you to create a SQLite database to store information about their employees.

1. Create a database that is saved on disk.

1. Create a table titled `employees` with the following columns:
  - id, firstName, lastName, jobTitle, address

1. Create an array of at least 6 objects. Each object should have a key value pair matching each column name in the `employees` table.
  ```js
  eg: let array = [
    { id: 0, firstName: 'Fred', lastName: 'Smith', jobTitle: 'Cashier', address: '500 Somewhere Lane' },
    ...,
  ]
  ```  

1. Insert each of the employee objects into the database.

1. Write a statement to query the database and `console.log()` all employee records.

1. Write a statement to query the database and `console.log()` each employees `jobTitle`.

1. Write a statement to query the database and `console.log()` each employees `firstName`, `lastName` and `address` only.

## Bonus Features

1. Update the employees table so that is has a `salary` column. Then update each employee record with a value for `salary`.

1. Write a statement that returns all employees of a certain `jobTitle`.
