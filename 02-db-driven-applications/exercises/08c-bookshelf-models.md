#Models

Models are a representation in our code, of how our data is structured in our databse.

you: But, my migration files give me all that information!
me: models can validatea your data
you: I can run queries without them!
me: but you shouldn't

We will use [Bookshelf](http://bookshelfjs.org/) to create  our models.

So far, in order to run our migrations and seed our databse, we've been using the knex cli to interact with our database, so this will be our first time actually requiring knex and bookshelf in our code.

Since bookshelf relies on knex, we need to do the following:
1. require knex, 
1. pass it our knexfile as the config, 
1. and save it to a variable
1. pass our knex variable to bookshelf, and save *that* as a variable

```
const env = process.env.NODE_ENV || 'development';
const config = require('./knexfile');
const knex = require('knex')(config[env]);
const bookshelf = require('bookshelf')(knex);
```

When you create a model, you use the following format. The only required  property is tableName, so this model is valid.

```
const Monster = bookshelf.Model.extend({
  tableName: 'monsters'
});
```

But how can this model be useful? We can use the bookshelf model plus bookshelf queries to easily create and add properties to a new monster without writing raw sql.
```
var monster = new Monster();  
monster.set('name', 'Sully');  
monster.set('variety', 'movie character');  

monster.save().then(function(m) {  
    console.log('Monster saved:', m.get('monster_name'));
});

```