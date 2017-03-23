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
let monster = new Monster();  
monster.set('name', 'Sully');  
monster.set('variety', 'movie character');  

monster.save().then(function(m) {  
    console.log('Monster saved:', m.get('monster_name'));
});

```

You can also add methods and relationships to your models. For example:
```
let Battle = bookshelf.Model.extend({
  tableName: 'battle',
  monster: function() {
    return this.belongsTo(monster);
  },
  hero: function() {
    return this.belongsTo(hero);
  }
},{
  byLocation: function(location) {
    return this.forge().query({where:{ location: location }}).fetch();
  }
});
```

Now we can run sweet code like this to see which monster and hero battled at Rhodes
```
Battle.byLocation('Rhodes').then(function(u) {  
    console.log('Got battle:', u.get('monster_id'), u.get('hero_id'));
});
```

and we can get our monster along with all related battles in a single query, like so:

```
Monster.forge({monster_name: 'Minotaur'}).fetch({withRelated: ['battles']})  
.then(function(monster) {
    console.log('Got monster:', monster.get('monster_name'), monster.get('monster_id'));
    console.log('Got battles:', monster.related('battles').toJSON());
});
```

###Collections

In Bookshelf you also need to create a separate object for collections of a given model. So if you want to perform an operation on multiple Monsters at the same time, for example, you need to create a Collection.

```
var Monsters = bookshelf.Collection.extend({  
    model: Monster
});

Monsters.forge().fetch().then(function(monsters) {  
    console.log('Got a bunch of monsters!');
    monsters = monsters.toJSON()
    console.log("My awesome json monsters", monsters)
});
```

###Exercise

Go do some jumping jacks






