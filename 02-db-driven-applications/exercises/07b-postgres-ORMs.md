<!-- Knex/bookshelf stuff -->
#ORMs

According to wikipedia, ORM (object-relational mapping) "is a programming technique for converting data between incompatible type systems in object-oriented programming languages." In plain English, we use ORM tools to get our databases to talk to our code, even though the database speaks SQL (or Mongo) and our code is writted in JavaScript.

###Knex

We will be using two different tools to interact with our PostgresSQL database. The first tool is Knex. Knex is useful for creating and managing our migrations, seeding the database, and creating queries. Knex can be used by itself, or in conunction with bookshelf.

###Bookshelf

Bookshelf is a JavaScript ORM for Node.js, built on the Knex SQL query builder. Bookshelf *cannot* be used without also using Knex. Bookshelf is the tool we will use to create models of our data and also query the database.

###Queries

So far, we've only used raw SQL to query our database. With the addition of knex and bookshelf, we now have two more options for how to query the database.  In general, your preference should be to write your queries in bookshelf, only using Knex when you can't accomplish something in bookshelf, and then only using raw SQL when neither bookshelf nor Knex will accomplish what you need to do.


###Resources
[ORM Wikipedia page](https://en.wikipedia.org/wiki/Object-relational_mapping)
[Knex](http://knexjs.org/)