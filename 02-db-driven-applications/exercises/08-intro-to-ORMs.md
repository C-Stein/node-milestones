#ORMs

According to wikipedia, ORM (object-relational mapping) "is a programming technique for converting data between incompatible type systems in object-oriented programming languages." In plain English, we use ORM tools to get our databases to talk to our code, even though the database speaks SQL (or Mongo) and our code is writted in JavaScript.

###Knex

We will be using two different tools to interact with our PostgresSQL database. The first tool is Knex. Knex is useful for creating and managing our migrations, seeding the database, and creating queries. Knex can be used by itself, or in conjunction with bookshelf.

###Bookshelf

Bookshelf is a JavaScript ORM for Node.js, built on the Knex SQL query builder. Bookshelf *cannot* be used without also using Knex. Bookshelf is the tool we will use to create models of our data and also query the database.

###Queries

So far, we've only used raw SQL to query our database. With the addition of knex and bookshelf, we now have two more options for how to query the database.  In general, your preference should be to write your queries in Bookshelf, only using Knex when you can't accomplish something in Bookshelf, and then only using raw SQL when neither Bookshelf nor Knex will accomplish what you need to do.

There is an elightening blog post/tutorial appropriately called [Using Bookshelf With Node.js](http://billpatrianakos.me/blog/2016/08/28/using-bookshelf-with-node-dot-js/) you might read for more insight. It's a bit ranty/potty-mouthed, so be forewarned. But it does nicely sum up how this symbiotic relationship works
  >"Without Knex you can’t have database migrations and connections. Without Bookshelf you can’t use the M in MVC. So no models for you. But together they make a great pairing. Bookshelf wraps around the Knex API and creates JavaScript objects (as in class instances) which can be saved as rows and relations in your database through Knex. Knex can then, in turn, generate an SQL query your database can understand."

The next few exercises will get you up and running with using Knex and Bookshelf to interact with PostgreSQL in a Node.js app.

###Resources
[ORM Wikipedia page](https://en.wikipedia.org/wiki/Object-relational_mapping)  
[Knex](http://knexjs.org/)  
[Bookshelf](http://bookshelfjs.org/)  
