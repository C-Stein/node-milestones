# PostgreSQL

PostgreSQL is a powerful, open source object-relational database system. As a database server, its primary function is to store data securely, and to allow for retrieval at the request of other software applications.


## Setup

Installation for Macs: follow the steps [here.](http://postgresapp.com/documentation/)

Installation for Linux: follow the steps [here.](https://www.postgresql.org/download/linux/)

Installation for Windows: follow the steps [here.](https://www.postgresql.org/download/windows/)


```
On install the following will become your default PostgreSQL settings:

Host:	localhost
Port:	5432
User:	your system user name
Database:	same as user
Password:	none
Connection URL:	postgresql://localhost
```


# psql

The primary front-end for PostgreSQL is the `psql` command-line program, which can be used to enter SQL queries directly, or execute them from a file. For now, we will use `psql` to get introduced to PostgreSQL.

To start using the program, make sure the PostgreSQL server is running. If it is, there should be an elephant icon in your toolbar. To open the `psql` interface, click on the elephant icon and select `Open psql`. This will open a new window in your terminal with `psql` running.

You should see something like this:
```
psql (9.6.0)
Type "help" for help.

yourusername=#
```

Helpful commands for `psql`:
- \h : list of all SQL commands available
- \? : list of all psql commands available
- \q : quit and exit psql


### Creating a Database with psql

First, lets get familiar some basic commands. Run the following command in your prompt: `username=# \l`

This will output a list of all of your PostgreSQL databases.

```
List of databases
  Name    |  Owner   | Encoding | Collate | Ctype |   Access privileges   
-----------+----------+----------+---------+-------+-----------------------
postgres  | postgres | UTF8     | C       | C     |
template0 | postgres | UTF8     | C       | C     | =c/postgres          +
          |          |          |         |       | postgres=CTc/postgres
template1 | postgres | UTF8     | C       | C     | =c/postgres          +
          |          |          |         |       | postgres=CTc/postgres
(3 rows)
```



\l - list databases
psql - CREATE DATABASE testdb;
\c testdb - this will connect you to db. must connect to db to run commands
DROP DATABASE name - cannot be used while connected to database
\d - list all tables in a attached db
\d tableName - will list the table
YOU DONT HAVE TO USE CAPS!!!
must follow SQL statements with semi-colons


### Additional Resources

[PostgreSQL Tutorial](https://www.tutorialspoint.com/postgresql/index.htm)
