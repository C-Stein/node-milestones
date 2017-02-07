# SQLite Practice

In this exercise you will create a SQLite database, create tables, insert records to the table, and query the database. We will be using the npm module [sqlite3](https://www.npmjs.com/package/sqlite3).

## Setup

```
mkdir sqlite101
cd sqlite101
npm install sqlite3 --save
touch sqlite3.js
```

## Instructions

A friend has asked for a favor. Using your NodeJS skills, they want you to create a SQLite database to store information about their employees.

1. Create a database that is saved on disk.

1. Create a table titled `employees` with the following columns:
  - id, firstName, lastName, department, address

1. Create an array of at least 6 objects. Each object should have a key value pair matching each column name in the `employees` table.
  ```js
  eg: let array = [
    { id: 0, firstName: 'Fred', lastName: 'Smith', department: 'Wildlife', address: '500 Somewhere Lane' },
    ...,
  ]
  ```  

1. Insert each of the employee objects into the database.

1. Write a statement to query the database and `console.log()` all employee records.

1. Write a statement to query the database and `console.log()` each employees department name.

1. Write a statement to query the database and `console.log()` each employees `firstName`, `lastName` and `address` only.

## Bonus Features

1. Update the employees table so that is has a `salary` column. Then update each employee record with a value for `salary`.

1. Update the employee array so that there are only 4 different departments. When console logging each department name, make sure that there are no duplicates.
