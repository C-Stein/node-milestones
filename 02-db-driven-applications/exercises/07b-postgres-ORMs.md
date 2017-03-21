<!-- Knex/bookshelf stuff -->
#ORMs

According to wikipedia, ORM (object-relational mapping) "is a programming technique for converting data between incompatible type systems in object-oriented programming languages." In plain English, we use ORM tools to get our databases to talk to our code, even though the database speaks SQL (or Mongo) and our code is writted in JavaScript.

###Knex

We will be using two different tools to interact with our PostgresSQL database. The first tool is Knex. Knex is useful for creating and managing our migrations, seeding the database, and creating queries. Knex can be used by itself, or in conunction with bookshelf.

###Bookshelf

Bookshelf is a JavaScript ORM for Node.js, built on the Knex SQL query builder. Bookshelf *cannot* be used without also using Knex. Bookshelf is the tool we will use to create models of our data and also query the database.

###Queries

So far, we've only used raw SQL to query our database. With the addition of knex and bookshelf, we now have two more options for how to query the database.  In general, your preference should be to write your queries in Bookshelf, only using Knex when you can't accomplish something in Bookshelf, and then only using raw SQL when neither Bookshelf nor Knex will accomplish what you need to do.

###Seeding

You've seeded data before, but

###Migrations

Have you noticed yet how wonderful github is? And have you also noticed how difficult it is to track  your database in github? Migrations to the rescue! Migrations allow us to create our databases and then track changes in the database in our javascript files.

According to [Wikipedia](https://en.wikipedia.org/wiki/Schema_migration)"A schema migration is performed on a database whenever it is necessary to update or revert that database's schema to some newer or older version. Migrations are performed programmatically by using a schema migration tool."

In order use migrations with Knex, you need to install Knex globally `npm install knex -g`. Since this is a global install, you will only need to so it once.

Like our dear friend, npm, you will need to `knex init` to create a knexfile.js. The knexfile will connect our app to our database and will sepcify any settings we want to use.

After that, you can create migrations `knex migration:make migration_name`, run migrations `knex migrate:latest`, and rollback migrations `knex migrate:rollback`.

So, what does all that stuff *mean*? 

####Creating a migration

Unlike other files in your project, knex will create your migration files for  you. Knex is very hepful and creates the migrations file with the name you specify in `knex migration:make migration_name` along with a timestamp. KNex will even go one step farther, and create a db/migrations directory for your migration files.

The migration file Knex creates for you includes two empty functions.



###Resources
[ORM Wikipedia page](https://en.wikipedia.org/wiki/Object-relational_mapping)
[Knex](http://knexjs.org/)
[Bookshelf](http://bookshelfjs.org/)